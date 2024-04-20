## はじめに

Gitプロジェクトでリモートリポジトリの向き先を変更することは、プロジェクトの管理を切り替えたり、バックアップのために異なるプラットフォームに移行したりする際に必要です。この記事では、既にGitLabに設定されているリモートリポジトリの向き先をGitHubに変更する手順を紹介します。

## 1. 現在のリモートリポジトリを確認

まず、現在設定されているリモートリポジトリの状態を確認します。これは `git remote -v` コマンドで行います。このコマンドは、設定されているリモートリポジトリの名前とURLを表示します。

```bash
git remote -v
```

出力例：

```
origin  https://gitlab.com/username/project.git (fetch)
origin  https://gitlab.com/username/project.git (push)
```

## 2. リモートリポジトリのURLを変更

次に、リモートリポジトリのURLをGitHubのものに変更します。これには `git remote set-url` コマンドを使用します。`origin` という名前のリモートリポジトリのURLを新しいものに置き換えます。

```bash
git remote set-url origin https://github.com/your-username/your-repository.git
```

このコマンドを実行後、再び `git remote -v` コマンドでURLが正しく変更されたことを確認します。

出力例：

```
origin  https://github.com/your-username/your-repository.git (fetch)
origin  https://github.com/your-username/your-repository.git (push)
```

## 3. 新しいリモートリポジトリにプッシュ

最後に、新しいリモートリポジトリに対してコードをプッシュして、変更が正しく反映されているかを確認します。

```bash
git push origin master
```

もし `master` ブランチがなく、`main` ブランチを使用している場合は、`master` の部分を `main` に置き換えてください。

## まとめ

この手順により、GitLabからGitHubにリモートリポジトリの向き先を簡単に変更することができます。これにより、リポジトリの管理をより柔軟に行うことが可能になります。
