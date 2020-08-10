---
title: "SCSSを使用しているHugoテーマのカスタマイズでハマった話"
date: 2020-08-10T07:29:26Z
lastmod: 2020-08-10T07:29:26Z
draft: false
keywords: []
description: ""
tags: [hugo]
categories: []
author: ""

# You can also close(false) or open(true) something for this content.
# P.S. comment can only be closed
comment: false
toc: false
autoCollapseToc: false
postMetaInFooter: false
hiddenFromHomePage: false
# You can also define another contentCopyright. e.g. contentCopyright: "This is another copyright."
contentCopyright: false
reward: false
mathjax: false
mathjaxEnableSingleDollar: false
mathjaxEnableAutoNumber: false

# You unlisted posts you might want not want the header or footer to show
hideHeaderAndFooter: false

# You can enable or disable out-of-date content warning for individual post.
# Comment this out to use the global config.
#enableOutdatedInfoWarning: false

flowchartDiagrams:
  enable: false
  options: ""

sequenceDiagrams: 
  enable: false
  options: ""

---

このWebサイトは、静的サイトジェネレータのHugoで作成している。
Hugo用のテーマが多数公開されていて、このサイトも「even」というブログテーマを使用している。
このテーマをカスタマイズしようとしてハマった話。

 <!--more-->

Hugoのテーマをカスタマイズする場合、テーマフォルダ(今回はthemes/even)に格納されているファイルを、テーマフォルダ以下のファイルパスを保ったまま、hugoプロジェクトのルートにコピーし、ファイルを編集する。

> コピー元: (略)/themes/even/assets/sass/_variable.scss  
> コピー先: (略)/assets/sass/_variable.scss

例えば、evenのカラーテーマを変更する場合、_variable.scssの$theme-color-configを、編集する。

```scss
// ========== Theme Color ========== //
// Config here to change theme color
// Default | Mint Green | Cobalt Blue | Hot Pink | Dark Violet
$theme-color-config: 'Default';
```

こんな感じで、簡単にテーマのカスタマイズを行えるのが、自分の環境だとカスタマイズが一向に反映されない。。

結局、解決策が見つからず、しばらく放置していたが、ようやく原因が判明。

Hugoには、無印HugoとHugo extendedという2つの種類があり、(手っ取り早く？)SCSSをコンパイルするにはHugo extendedが必要らしい。なぜカスタマイズしてなかったときには無印Hugoで動いていたのかはよくわからない。。

というわけで、Hugo extendedをインストールして、hugo serverしてみたところ、カラーテーマがちゃんと変更されていた。ついでにフォントとかも変更できて満足。

というお話でした。

### 参考リンク

* [Hugo Releases(Github)](https://github.com/gohugoio/hugo/releases)

    配布物の一覧に、hugo_extendedがある。
