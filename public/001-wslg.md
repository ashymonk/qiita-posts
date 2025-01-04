---
title: WSLg の仕組みを理解する
tags:
  - WSL
  - WSL2
  - WSLg
  - Linux
  - weston
private: false
updated_at: ''
id: null
organization_url_name: null
slide: false
ignorePublish: false
---
WSLg の仕組みを調査しています。記録としてメモしていきます。
# WSLg とは？
**WSLg (Windows Subsystem for Linux GUI)** とは、WSL ディストリビューション上の Linux GUI アプリケーション（X11, Wayland）を Windows へ統合する機能です。この機能により、ディストリビューションにインストールした GUI アプリ（xterm, GVim, firefox, etc...）が、他の Windows アプリと同様の感覚で操作できるようになります。WSLg が導入される以前で GUI アプリを実行するには、Windows ホストで X11 サーバを起動して、ディストリビューションの DISPLAY 変数にホストの X11 サーバを設定（もしくはSSHでX転送）する必要がありました。

# 魔法を解明する
WSLg の仕組みを調べていきます。量が多くなった場合は複数の記事に分割する予定です。

# まずは README を読む

https://github.com/microsoft/wslg

WSLg 公式リポジトリにドキュメントがある程度まとまっており、アーキテクチャの説明があります。要点をまとめていきます。

## アーキテクチャ

![WSLg_ArchitectureOverview.png](https://github.com/ashymonk/qiita-posts/blob/feature/1-wslg/public/images/001-wslg/WSLg_ArchitectureOverview.png?raw=true)
