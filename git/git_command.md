# 初期設定
## Git リポジトリの初期化（新規作成）
git init

## 既存のリポジトリをクローン（コピー）
git clone <リポジトリURL>

## 変更されたファイルの状態を確認
git status

# ステージング・コミット
## すべての変更をステージング（インデックスに追加）
git add .

## 特定のファイルのみステージング
git add <ファイル名>

## コミット（ステージングされた変更を確定）
git commit -m "コミットメッセージ"

## ステージングを取り消す
git reset HEAD <ファイル名>

## 直前のコミットを修正（まだ push していない場合）
git commit --amend -m "修正したメッセージ"

# ブランチ操作
## 現在のブランチを表示
git branch

## 新しいブランチを作成
git branch <ブランチ名>

## ブランチを切り替える
git checkout <ブランチ名>
git switch <ブランチ名>  # (推奨)

## ブランチを作成してすぐに切り替える
git checkout -b <ブランチ名>
git switch -c <ブランチ名>  # (推奨)

## ブランチを削除（ローカル）
git branch -d <ブランチ名>

## ブランチを削除（強制）
git branch -D <ブランチ名>

# マージ・リベース
## ブランチをマージ（現在のブランチに指定ブランチを統合）
git merge <ブランチ名>

## マージコミットを作らずに統合（リベース）
git rebase <ブランチ名>

## リベース時のコンフリクトを解決後、リベースを続行
git rebase --continue

## リベースを中止
git rebase --abort

# ログ・履歴管理
## コミット履歴を表示
git log

## 簡潔な履歴を表示
git log --oneline --graph --decorate --all

## 直近の変更を確認
git diff

# コミットの取り消し
## 直前のコミットを取り消し（変更は残す）
git reset --soft HEAD^

## 直前のコミットを取り消し（変更をステージングから外す）
git reset --mixed HEAD^

## 直前のコミットを完全に取り消し（変更も削除）
git reset --hard HEAD^

## すでに push したコミットを取り消し（リモートも強制上書き）
git push origin <ブランチ名> --force

# ファイルの管理
## 特定のファイルを Git の管理から外す（削除はしない）
git rm --cached <ファイル名>

## 追跡対象のファイルを削除（リポジトリとローカル両方から削除）
git rm <ファイル名>

# タグ
## タグを作成
git tag <タグ名>

## タグをリモートにプッシュ
git push origin <タグ名>

## タグ一覧を表示
git tag
