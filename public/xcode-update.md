---
title: 【macOS】Xcodeをアップデートしたのにxcodebuildのバージョンが古いままの時の対処法
tags:
  - Xcode
  - macOS
  - xcode-select
  - xcodebuild
  - 備忘録
private: false
updated_at: "2025-06-26T10:17:21+09:00"
id: ee8e8676f841ae8000e3
organization_url_name: null
slide: false
ignorePublish: false
---

## はじめに

macOSで開発をしていると、「App StoreでXcodeを最新版にアップデートしたはずなのに、ターミナルでバージョンを確認すると古いまま」という問題に遭遇することがあります。

この記事では、その原因と解決策を備忘録として残します。

## 1. 現在のコマンドラインツールのバージョンを確認

まず、ターミナルで現在設定されている`xcodebuild`のバージョンを確認します。`xcodebuild -version` コマンドを使用します。

```bash
xcodebuild -version
```

**出力例（問題発生時）：**

```
Xcode 15.4
Build version 15F31d
```

このように、インストールしたはずの新しいバージョンが反映されていないことがあります。

## 2\. コマンドラインツールの参照先を変更

次に、コマンドラインツールが参照するXcodeのパスを、新しいバージョンに切り替えます。これには `xcode-select` コマンドを使用します。

```bash
sudo xcode-select -s /Applications/Xcode.app/Contents/Developer
```

このコマンドは管理者権限（`sudo`）で、コマンドラインツールが参照すべきパス（`-s`）を、新しくインストールしたXcode（`/Applications/Xcode.app`）に設定しています。

コマンド実行後、再度バージョンを確認してみましょう。

```bash
xcodebuild -version
```

**出力例（解決後）：**

```
Xcode 16.4
Build version 16F6
```

バージョンが正しく更新されていることが確認できました。

## 3\. GUIから設定する方法

この設定は、XcodeのGUIからも変更することが可能です。

1.  新しいXcodeアプリケーションを開きます。
2.  メニューバーから **`Xcode` \> `Settings...`** を選択します。
3.  **`Locations`** タブを開きます。
4.  **`Command Line Tools`** のドロップダウンメニューから、目的のXcodeバージョンを選択します。

基本的には、手順2のコマンド実行と同じ結果が得られます。

## まとめ

Xcodeをアップデートしてもターミナルのバージョンが古いままの場合は、`xcode-select`コマンドで参照先のパスを明示的に切り替えることで解決できます。この手順はmacOSの開発環境をセットアップする際によく必要となるため、覚えておくと便利です。
