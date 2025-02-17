# GitHub リポジトリ作成

## リポジトリ作成・クローン
1. GitHubで新しいリポジトリを作成。
2. `.gitignore`は`Node`を選択（ReactやJSのプロジェクトの場合）。
3. `README.md`を作成しておく。
4. ターミナルを開いて、クローンするディレクトリに移動。
5. git clone https://github.com/username/study-react-hooks.git
6. cd study-reaact-hooks
7. code .

## GitHubのアカウントを変更する場合（Windowsの場合）
1. PowerShellを開く。
2. cmdkey /delete:git:https://github.com
3. キャッシュされたGitの認証情報が削除される。
4. git pushする際、新しい認証情報が求められる。