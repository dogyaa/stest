### 4. Windows 10 で動かしてみた

2003 年当時に作成した自作シューティングゲーム (STG) ですが、Windows 7 では画面が一部バグってしまい、Windows 10 では画面が全く映らず、まともにプレイできなくなっていました。

「画面が真っ暗だけど音だけは聞こえる (よって動いてはいるらしい)」という様子を見ていただこうと思い、Windows 10 の標準機能である [XBox Game Bar](https://support.xbox.com/ja-JP/help/games-apps/game-setup-and-play/get-to-know-game-bar-on-windows-10) を使って、Windows 10 ( Intel CPU 製 CPU & NVIDIA 製グラフィックボード) PC 上で STG を動かして適当に操作した様子を撮影してみたのですが…

実際の画面は真っ暗 (というよりもモニタが映像を拾っていない) にも関わらず、録画された映像には、壮絶にバグってはいるものの、ゲームが動いていることが確認できてしまいました。



https://user-images.githubusercontent.com/93638420/171535036-8ebfcce2-0d52-484e-ae5f-1457422831be.mp4



Windows 10 では画面が全く表示されないと思っていたのですが、どうやら Alt + Tab や Windowsキー + Tab で表示される起動中のソフトウェア一覧から STG の実行ファイル (と思われる、画面が真っ暗なもの) を選ぶと、バグってはいますが一応ゲーム画面が表示されるようです。

うすうす感じていたことではあるのですが、これらのバグは Hot Soup Processor (HSP) の [DirectX](https://ja.wikipedia.org/wiki/Microsoft_DirectX) に関するプラグインのバージョンの問題であり、これが最近の Windows やグラフィックドライバでは正しく動かないのが原因ではないかと思っていました。

そのまま何年も「仕方がない」と放置していたのですが、[ここ](https://github.com/stest10/stest/blob/main/articles/stest1.md)で書いているように、最近になってからお笑いコンビ[マヂカルラブリー](https://profile.yoshimoto.co.jp/talent/detail?id=2772)の[野田クリスタル](https://profile.yoshimoto.co.jp/talent/detail?id=2773)氏が制作したゲーム、通称[野田ゲー](https://www.youtube.com/channel/UCzfagYm_ai4JjGBRedqxu9Q)が同じ言語 HSP で作られていることを知り、「今も幅広く使われている言語なのだから、調べればバグを直す方法が見つかるのでは」と、改めてバグ修正のための調査を始めることになりました。

そしてついに、[同じバグに関する報告とその修正方法について紹介しているページ](https://note.com/ukio_uki/n/n343991c1f2e0)を見つけたのです…！！

上の方と同じく、私も[ここ](https://silight.hatenablog.jp/entry/2018/05/21/221355)で紹介されているパッチでは改善せず、[ここ](https://github.com/narzoul/DDrawCompat/releases)から `DDrawCompat-v0.3.1.zip` をダウンロードして、`ddraw.dll` ファイルを置き換えてから STG を実行したところ、グラフィックのバグが直って正しく動作するようになりました。私の場合はちょっとした表示のバグも今のところ見つからず、完全に動作しているようです。

まあ、時々正常起動に失敗して真っ暗な画面になってしまうのですが、その時は上で書いたのと同様に、Alt + Tab や Windowsキー + Tab を使って画面が表示させられます。また `ddraw.dll` を置き換える前は、起動時の画面は必ず真っ暗だったのに対して、置き換えた後は必ずしもそうではなく、最初からゲーム画面が表示されることも多いようです。原因や対処方法がはっきりと分かっておらず、ごめんなさい。



https://user-images.githubusercontent.com/93638420/171535089-b31d680a-73b3-41b7-947d-8eee6cd58ed4.mp4


画面の右上に NVIDIA のメッセージが一瞬表示されてしまっていますがご容赦下さい。

上の動画ではキーボードを使って適当に動作確認をしていますが、USB/Bluetooth 接続のゲームパッドでも動かせることを確認しています。
しかし…今回は PS4 タイプのコントローラーを試したのですが、自機の移動に割り当てられているのは十字キーではなく、このスティック部分になっているようです。

![](https://github.com/stest10/stest/blob/main/ss/4_1.png?raw=true)

(画像は[ソニーストア](https://pur.store.sony.jp/ps4/products/ps4_controller/CUH-ZCT2J_product/)からダウンロードしたものに一部加工を施しています。このコントローラーそのものを使っているわけではありません。)

[ここ](https://github.com/stest10/stest/blob/main/articles/stest2.md)で書いているように、この STG はコンフィグ設定によってキーの割り当てを変更することができるのですが、残念ながら方向キーの割り当ては変えられるようになっていません。私はファミコンやスーパーファミコンの世代であり、この手のスティック操作にはなれていないので、できれば十字キーに割り当てたかったのですが。。

2003 年当時はまだスクエアモニタが一般的で、最近普及しているワイドモニタだとタイトル画面が横に間延びしてしまっていますが、プレイ中の画面では右側にステータス画面が表示されるようになっているためか、あまり気になりません。
本 STG はフルスクリーン表示にしか対応しておらず、ウィンドウ表示で遊ぶことができないのは少し残念です。

ソースコードは見つかっているので、ウィンドウ表示や方向キーの割り当てについても改良できなくはないのかもしれませんが、凄まじいスパゲッティコードのため手がつけられそうにありません。。ソースコードや開発環境についてもいずれ紹介したいと思います。