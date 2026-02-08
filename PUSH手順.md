# GitHubにpushする手順

## 1. GitHubでリポジトリを作成

1. https://github.com/new にアクセス
2. リポジトリ名: `espict-repo` (または任意の名前)
3. **Private** を選択（社内資料なので推奨）
4. **「Initialize this repository with a README」はチェックしない**（既にローカルにコミット済みのため）
5. 「Create repository」をクリック

## 2. リモートを追加してpush

GitHubでリポジトリ作成後、表示されるURL（例: `https://github.com/ユーザー名/espict-repo.git`）を使って以下を実行：

```bash
cd /Users/mjup/espict-repo
git remote add origin https://github.com/ユーザー名/espict-repo.git
git branch -M main
git push -u origin main
```

## 3. 認証が必要な場合

- **HTTPSの場合**: GitHubのPersonal Access Tokenが必要
- **SSHの場合**: SSH鍵を設定して `git@github.com:ユーザー名/espict-repo.git` を使う

## 4. 他PCでcloneする場合

```bash
git clone https://github.com/ユーザー名/espict-repo.git
cd espict-repo
```
