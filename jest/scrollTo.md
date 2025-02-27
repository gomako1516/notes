# Jestでスクロール位置を検証するには？

ページ遷移後、スクロール位置が先頭に戻る処理が正しく機能しているか？を確認するテストを構築していたとき、詰まってしまった。  
Jestのテスト環境（jsdom）では、scrollToがサポートされていないため、単純にJSでスクロール位置を操作しようとしても反映されない。  
テスト環境でscrollToをモックする必要がある。

## scrollToの動作を手動で変更できるようにする

JSの`Object.defineProperty()`を使用して、scrollToの設定を変更する。  
以下が基本的な書き方。  
設定オプションを変更して、「読み取り専用」や「上書き禁止」にできる。

```
Object.defineProperty(オブジェクト, "プロパティ名", {
  設定オプション
})
```

以下のように、scrollToの動作を「手動で変更」できるようにする。

```
Object.defineProperty(HTMLElement.prototype, "scrollTo", {
  // スクロール位置の上書きを許可
  writable: true,

  // スクロール位置の上書き処理
  value: function (options: { top: number }) { // オプションの'top'を取得
    this.scrollTop = options.top // 'scrollTop'を'top'の値に変更
  },
})
```

## 例）スクロール位置が先頭に戻っているかのテスト

ボタンをクリックして遷移したあと、スクロール位置が先頭に戻っているかを検証。  
事前にスクロール位置を変更しておく必要がある。

```
test('スクロール位置が先頭に戻る。', async () => {
  Object.defineProperty(HTMLElement.prototype, 'scrollTo', {
    writable: true,
    value: function (options: { top: number }) {
      this.scrollTop = options.top
    },
  })

  render( <TestComponent /> )

  // スクロールできるように画面高を調整
  const scrollBody = screen.getByTestId('scroll-body')
  Object.defineProperty(scrollBody, 'scrollHeight', { value: 400 })

  // スクロール位置を50にする
  scrollBody.scrollTop = 50
  fireEvent.scroll(scrollBody)

  // 現在のスクロール位置を確認
  expect(scrollBody.scrollTop).toBe(50)

  // ボタンをクリック
  const linkButton = screen.getAllByTestId('link-button')
  fireEvent.click(targetBreadcrumb)

  // スクロール位置が先頭に戻っているかを確認
  expect(scrollBody.scrollTop).toBe(0)
})
```

describeでグループ化したテスト内全てでスクロール位置の検証を行う場合、`Object.defineProperty()`の設定は`beforeEach()`の中ですると良い。

## まとめ
スクロール位置を検証するための手順は頭にあったけれど、実際に構築してみると詰まってしまった。  
Jestが用意しているテスト環境では対応しきれないこともあるので注意が必要ですね。
