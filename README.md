# モーダルウィンドウの実装方法の紹介

モーダルウィンドウ（または、ポップアップとかダイアログ？）の実装方法を色々紹介しつつ、コードについて解説をしたいと思います。


## はじめに

世の中にはモーダルウィンドウのライブラリが色々でていると思うのですが、実は、*要件によっては*自前で実装したほうが都合がいいことがあったりします。

### 自前で実装することのメリット

しごく当たり前になってしまいますが、以下のようなメリットがあります。

* モーダルウィンドウのデザイン変更がしやすい。（CSSを適用しやすいという意味で。）
  ※ライブラリを使うと、どの要素にどんなクラスがかかっていて。。。というのが、把握しづらかったり、オプション設定すると、またクラスが変わったり。。など、HTMLにどんなクラスがあたるかの把握が必要になる場合があります。
* Javascriptのソースが把握しやすい、改修がしやすい。
  ※自分が作ったソースだし。ただ、改修しやすいかは、ソースの作り方によります。
* Javascriptの全体容量が軽くなる（ことがある。要件次第。）
  ※ライブラリを使うと必要のない処理まで入っていることがあり、その分ソース容量が重くなる、ということ。

一方、もちろんデメリットもあります。

### 自前で実装することのデメリット

* 手軽さはない。
  ※ライブラリの場合、モーダルウィンドウのデザインパターンまで用意してくれている場合がありますが、自前実装の場合は、ここも1から作る必要があります。
* 複雑な機能を実装するなら、ライブラリの使用が◎。
  ※複雑な処理をしたい場合、もちろんその実装をするのは自分になります。複雑な処理をするということは、バグを生みやすかったり、ブラウザ表示による差異がでる可能性も高くなります。ライブラリは、サポートブラウザでの動作保障がある程度あるので、やはり複雑な処理はライブラリを使ったほうがよかったりします。

ここで言いたいことをざっくりまとめると、

ライブラリ使ったほうが全体工数少なくなるなら使ったほうがいいけど、
ただ単に表示するだけのモーダルだったり、カスタマイズが多く発生しそうな場合は、自前で実装したほうがいいよ。

ってことです。

それでは、実装方法を見ていきたいと思います。


## モーダルウィンドウの実装方法

### 基本形

* HTML/CSS
* Javascript

### 応用編(1)

* スクロールしている場合は、表示中のウィンドウの位置にモーダルウィンドウが表示されるようにする
* モーダルウィンドウの高さ（＋上下余白値）が、ウィンドウの高さを超えた場合の処理
* ページ内に、静的なモーダルウィンドウを複数表示する
* モーダルウィンドウ下のレイヤーをクリックしたら、モーダルウィンドウを閉じる

### 応用編(2)

* モーダルウィンドウ内に、テンプレートを使って表示したい（一部だけ動的に書き換えてほしい）
* モーダルウィンドウを閉じずに、モーダルウィンドウ内のコンテンツを変える
* フェードインで表示、フェードアウト閉じる


### 番外編

* CSSだけでモーダルウィンドウを表示（閉じれないけど）
