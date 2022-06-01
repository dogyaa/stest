### 2. 仮想マシン上で動かしてみた

2021 年、古い PC の整理をしていた時に見つけた自作シューティングゲーム (STG) ですが、その古い PC のうちの一台である 2004 年製のノート PC の上で動作することは確認していました。
そこで当初は、この古いノート PC 上で STG を動かして、その様子をキャプチャーボードで Windows10 マシンに取り込もうと計画していました。とは言え、20 年近く前のノート PC だからか動作も不安定になっていますし、小さなキーボードでまともに STG のプレイをするのもなかなか難しいものがあります。

そんな中、ふと「Windows XP で動くんだったら、Windows XP をインストールした仮想マシンの上で動かせば良いのでは？」と思い付き、[Oracle VM VirtualBox](https://www.virtualbox.org/) 上で実験してみたところ無事に動作しました！


![](https://github.com/stest10/stest/blob/main/ss/2_1.png?raw=true)

VirtualBox の仮想マシン上で表示されたタイトル画面です。名前はまだありません。

<p><img src="https://github.com/stest10/stest/blob/main/ss/2_2.png?raw=true" width="480px"> <img src="https://github.com/stest10/stest/blob/main/ss/2_3.png?raw=true" width="480px"></p>

コンフィグ実行画面。STG 本体の実行の前に、まずはこちらで初期設定をします。操作はキーボード、ジョイパッド (ゲームパッド) のどちらにも対応しており、各キーの割り当てが出来ます。残念ながら、方向キーの設定は変更できないようです。

![](https://github.com/stest10/stest/blob/main/ss/2_4.png?raw=true)

「音関係」ボタンからサウンドの設定もできます。MIDI ファイルを準備しておけば BGM の再生も可能です。

<p><img src="https://github.com/stest10/stest/blob/main/ss/2_5.png?raw=true" width="480px"> <img src="https://github.com/stest10/stest/blob/main/ss/2_6.png?raw=true" width="480px"></p>

自機は 2 種類の中から選ぶことができます。

![](https://github.com/stest10/stest/blob/main/ss/2_7.png?raw=true)

ゲームプレイ中の各フレームの入力情報をとっておくことで、リプレイデータの保存と再生にも対応しています。Replay を選択すると過去のリプレイデータを再生でき、Record を選択すると既存のデータに新しいリプレイデータが上書きされます。


もう 20 年近くテレビゲーム (ビデオゲーム？コンピューターゲーム) を遊んでいない私には、今からこれを自分でプレイして最後までクリアするのはほぼ不可能なのですが、リプレイデータがあれば当時のテストプレイを再現できそうです。そこで、次はリプレイ動画の作成にチャレンジします。
