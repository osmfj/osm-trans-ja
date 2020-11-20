OpenStreetMap翻訳プロジェクト
===


[![hackmd-github-sync-badge](https://hackmd.io/bur_i2h7Rg6-pSIZnqzKew/badge)](https://hackmd.io/bur_i2h7Rg6-pSIZnqzKew)

OSM翻訳プロジェクトとは
---

OpenStreetMap は、イギリス発祥のグローバル活動で、そのドキュメントは世界中で利用できるように主として英語でまずは記述されることがおおい。
また、活動に必要なWebサイトや、ツールについても、はじめから国際化(インターナショナライズ)されて開発されており、原文の言語は英語である。世界中のOpenStreetMap貢献者は、それぞれの母国語などへ翻訳を実施してプロジェクトへ提供することで、各国語への地域化(ローカライズ)を実現しています。

日本のOpenStreetMapコミュニティでは、OSM Wiki上に翻訳プロジェクトを2007年に立ち上げ、ユーザにとって有益な文書やアプリケーションについて、日本語化(和訳)をすすめています。

なお、コミュニティには、各国語による各国活動のリソースも多量にあるため、全部を翻訳するものではないほか、オリジナルが日本語という文書も当然ながら存在します。

githubリポジトリについて
---

OpenStreetMap翻訳プロジェクトの[Githubリポジトリ](https://github.com/osmfj/osm-trans-ja) は、OSMの和訳プロジェクトのチーム活動をOmegaTのチーム機能により支援するためのものです。
WikiやJOSMの翻訳において、用語の統一、類似翻訳の活用により、効率化をはかります。


参加方法
---

一緒に活動いただける方はGithubのアカウントをつくり、プロジェクトページでIssueとして参加表明してください。```https://github.com/osmfj/osm-trans-ja/issues/new``` 書き込み権限をつけます。

書き込み権限がありますと、適宜OmegaTがリポジトリを更新するようになります。

Pull Requestには対応しませんので、ご注意ください。


リポジトリの利用方法
---


OmegaTには、チーム翻訳機能があります。OSM翻訳プロジェクトでは最新機能をつかっていますので、OmegaT の最新版（バージョン5.3以降）をインストールしてください。

OmegaTのメニューで、「プロジェクト（P)」ー「チームプロジェクトをダウンロード」を選択しリポジトリURLに```https://github.com/osmfj/osm-trans-ja.git``` を入力してください。


　もし、チーム参加を希望されない場合は、チームのダウンロードの代わりに、上記プロジェクトからZipファイルでダウンロードをして、そのフォルダをベースとして開始されるといいでしょう。（https://github.com/osmfj/osm-trans-ja/archive/master.zip)
 
  その場合でも、過去の翻訳成果を活用して効率よく翻訳作業をおこなうことができます。しかしながら、全体の統一感を出していく、用語を統一するなどに参加してもらうことで、他の方の作業に貢献できるので、チームへの参加を強く推奨します。

翻訳対象となる原文については、ダウロードされるプロジェクトのsource ディレクトリへ追加されています。Wikiについては、全部ではありませんので、自分が翻訳したい原文は自分自身で追加してください。

 Wikiの原文ダウンロードは、OmegaTの「ファイル」ー「MediaWikiから原文ファイルを追加(W)」を選択し、OSM WikiのURLを入力してください。



OmegaTの利用方法
===

OmegaTの利用方法については[HackMDで公開](https://hackmd.io/@osmfj/r14oK7MXv/https%3A%2F%2Fhackmd.io%2F%40osmfj%2FH1FAQy0mv)しています。

必要なプラグイン
---

* Okapi filters for OmegaT プラグインがTasking managerとMerkaatorの翻訳に必要です。 [リンク](https://okapiframework.org/wiki/index.php?title=Okapi_Filters_Plugin_for_OmegaT)
* 機械翻訳サポートの[OmegaT TexTra Plugin](https://github.com/miurahr/omegat-textra-plugin/releases) が推奨です。
* 辞書フォーマットサポートの [OmegaT plugin for EPWING dictionary](https://github.com/miurahr/omegat-plugin-epwing/releases) が推奨です。


推薦される辞書
---

* [ビジネス技術実用英語大辞典](http://www.hi-ho.ne.jp/unnos/unnodict.htm)を推薦します。


翻訳対象プロジェクト、ページ、情報源
===

JOSM
----

* プロジェクトURL: https://josm.openstreetmap.de/
* 翻訳プロジェクト: https://translations.launchpad.net/josm/trunk
* 翻訳への参加方法文書: https://josm.openstreetmap.de/wiki/Translations

iD Editor
---

* プロジェクトURL: http://ideditor.com/
* 翻訳プロジェクト: https://www.transifex.com/openstreetmap/id-editor/
* 翻訳への参加方法文書: https://github.com/openstreetmap/iD/blob/develop/CONTRIBUTING.md#translating

Merkaator Editor
---

* プロジェクトURL:　http://merkaartor.be/
* 翻訳プロジェクト: https://www.transifex.com/merkaartor/merkaartor/dashboard/
* 翻訳への参加方法文書：　https://wiki.openstreetmap.org/wiki/Merkaartor

OSM Wiki
----

* プロジェクトURL: https://wiki.openstreetmap.org/

* 翻訳作業に使用するファイルの取得: OmegaTのWikimediaからのダウンロード機能で取得する
* Wikiへの反映： 訳文ファイルをエディタでひらき、ブラウザからWikiへはりつけてを更新する。

Simple task manager
---

* https://github.com/hauke96/simple-task-manager

* 翻訳作業に使用するファイル: githubから取得
  * messages.ja.xlf: simple-task-manager_messages.ja.xlf に改名して追加されている
  * README.md, client/README.md, server/README.md: simple-task-manager_*_README.mdに改名して追加

* プロジェクトへの反映: 更新してPull-Requestを発行する


Tasking manager
---

* プロジェクトURL: https://github.com/hotosm/tasking-manager/
* 翻訳への参加方法: https://github.com/hotosm/tasking-manager/blob/develop/docs/contributing-translation.md
* 翻訳プロジェクト: https://www.transifex.com/hotosm/tasking-manager/dashboard/

* 翻訳作業に使用するファイル: github から取得した英語版jsonファイル
* Transifex更新に使用するファイル: TransifexからXLIFFをダウンロードし、Okapi pluginのXLIFFフィルタで生成した訳文XLIFFをアップロード


###### tags: `翻訳`, `OpenStreetMap`, `Wiki`, `翻訳`, `コミュニティ`
