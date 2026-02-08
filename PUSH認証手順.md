# GitHubへのpush認証手順

## 方法1: Personal Access Token（推奨）

### 1. GitHubでTokenを作成
1. https://github.com/settings/tokens にアクセス
2. 「Generate new token」→「Generate new token (classic)」をクリック
3. Note: `espict-repo-push` など任意の名前
4. Expiration: 適切な期間を選択（90日、1年など）
5. Scopes: **`repo`** にチェック（全てのリポジトリへのアクセス）
6. 「Generate token」をクリック
7. **表示されたトークンをコピー**（後で見れないので注意）

### 2. push時に使用
```bash
cd /Users/mjup/espict-repo
git push -u origin main
# Username: Mjup-ai
# Password: [コピーしたPersonal Access Tokenを貼り付け]
```

### 3. 認証情報を保存（オプション）
```bash
# macOS Keychainに保存（次回から自動認証）
git config --global credential.helper osxkeychain
```

## 方法2: SSH鍵を使用（より安全）

### 1. SSH鍵を生成（まだの場合）
```bash
ssh-keygen -t ed25519 -C "your.email@example.com"
# Enter連打でデフォルト設定
```

### 2. 公開鍵をGitHubに登録
```bash
cat ~/.ssh/id_ed25519.pub
# 表示された内容をコピー
```

1. https://github.com/settings/keys にアクセス
2. 「New SSH key」をクリック
3. Title: `MacBook` など任意
4. Key: コピーした公開鍵を貼り付け
5. 「Add SSH key」をクリック

### 3. リモートURLをSSHに変更
```bash
cd /Users/mjup/espict-repo
git remote set-url origin git@github.com:Mjup-ai/EspictAll.git
git push -u origin main
```

## 方法3: GitHub CLIを使用（最も簡単）

### 1. GitHub CLIをインストール
```bash
brew install gh
```

### 2. 認証
```bash
gh auth login
# ブラウザで認証
```

### 3. push
```bash
cd /Users/mjup/espict-repo
git push -u origin main
```

