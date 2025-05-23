# 似非²RAMカートリッジ(1Mbyte版)
[English README is here](README-en.md)

![](assemble_manual/front.jpg)
![](assemble_manual/rear.jpg)

これは、汎用ロジックICによりメガROMコントローラと同等の動作を実現し、それを利用して似非RAMを構築したMSX用カートリッジ(命名:似非・似非RAMまたは似非²RAM)です。
ごりぽんハードウェア(同人サークル・ごりぽんソフトウェアのハードウェア部門)により作成されました。

KiCAD7用の回路図データ・基板データ・ガーバーデータを、クリエイティブ・コモンズライセンス(CC-BY-NC)で公開しています。
[MGINST215.zip](https://github.com/goriponsoft/ESE2RAM-Cartridge-74670/blob/main/MGINST215.zip)および[KSAVER105.zip](https://github.com/goriponsoft/ESE2RAM-Cartridge-74670/blob/main/KSAVER105.zip)はCCライセンスの対象ではなく、元のライセンスと条件が適用されます。

X(旧Twitter): @goriponsoft

## 似非RAMディスク(似非RAM)とは？

[同人サークル・似非職人工房](http://www.hat.hi-ho.ne.jp/tujikawa/ese/)のつじかわ氏が考案した、ストレージなどとして使えるMSX用の汎用バックアップRAMカートリッジです。

通常は、ゲームのメガROMカートリッジを改造し、ROMをRAMに置き換えることで制作します。MGINSTコマンドによりDOSカーネルをインストールしてSSDのようなストレージとして利用したり(似非RAMディスク)、メガROMのイメージを読み込ませて動作させたりすることができます。

もともとストレージとしての使用を前提に考案されたため、カートリッジ自体も「似非RAMディスク」と呼ぶほうが一般的です。

なお、所有していないゲームのイメージを読み込ませて利用することは違法行為です。通常は似非RAMディスクの他、似非RAMに改造することで使用できなくなる改造元ゲームカートリッジのイメージ(改造前にファイルに書き出しておく必要あり)、フリーウェア、自作ROMゲーム、などを動作させるのに使用します。

似非RAMディスクについての詳細は、[似非職人工房の似非RAMディスクのページ](http://www.hat.hi-ho.ne.jp/tujikawa/ese/eseram.html)を参照してください。

## 似非²RAM(似非・似非RAM)とは？

近年MSXゲームの入手自体が難しくなり、貴重になってしまったメガROMカートリッジを潰して似非RAMにするのはかなり躊躇われる状況でした。そこで、普通に入手できる汎用ロジックICを使い、メガROMコントローラーと同等の回路を実現し、それを利用して似非RAMとして組み上げたのがこのカートリッジです。

似非RAMでありながら、メガROMコントローラを使用していない「似て非なる似非RAM」ということで「似非・似非RAM」、転じて「似非の2乗」で「似非²RAM」と命名しました。上付き文字の使用に問題がある場合は「似非2RAM」や「似非似非RAM」でも構いません。英語表記は「ESE-ESE-RAM」または「ESE2-RAM」です。

## 部品表
注意: 基板Rev.6以降U3～U5が74HCシリーズから74AHCシリーズに変更されています
|部品番号|内容|数量|
|:--|:--|--:|
|BT1|CR2032電池ホルダ "CH29-2032LF"/"CH28-2032LF(TR)"/"CH004-2032LF"/"CH004-2032LF"のいずれか|1|
|C1-C8|セラミックコンデンサ 0.1μF・50V・2.5mmピッチ|8|
|C9|電解コンデンサ 47μF・16V|1|
|D1-D2|ダイオード "1N4148"|2|
|IC1-IC2|4Mbit SRAM(628512タイプ・512K×8) DIP-32 "AS6C4008"など|2|
|R1-R4|抵抗 1/4W・10KΩ|4|
|RN1|集合抵抗 8素子・10KΩ SIP-9|1|
|S1|6×6mm タクトスイッチ "TVDP01-095BB1"|1|
|U1-U2|汎用ロジックIC "74HC670"|2|
|U3|汎用ロジックIC "74AHC138"|1|
|U4|汎用ロジックIC "74AHC00"|1|
|U5|汎用ロジックIC "74AHC32"|1|
|-|CR2032電池|1|

## 組み立て方
基板の実装面積の関係で、抵抗、コンデンサ、ダイオードなどの部品が裏面(ハンダ面)に配置されているため、組み立てには注意が必要です。

[詳細な組み立てマニュアル(日本語版)はこちら](assemble_manual/main.md)

1. 基板を裏返して(コネクタの傍に「Front」と書かれている側が表面です)、シルク印刷を参考に、ダイオード、抵抗、セラミックコンデンサ、集合抵抗、の順で部品を配置して表側(部品面)からハンダ付けします。ハンダを盛りすぎると、ICと基板の間に隙間ができるので、ハンダの量は控えめにしてハンダ付けしてください。
2. ハンダ付けしたら、表面に余ったリードを切断します。リードが余分に残っていると、やはりICと基板の間に隙間ができるので、こちらもできるだけ短くなるように切断してください。
3. 基板を表に戻し、IC、電解コンデンサ、セラミックコンデンサを配置し、通常通り裏面(ハンダ面)からハンダ付けしていきます。電解コンデンサはシルク印刷の方向に横倒しにして実装してください(縦に実装するとカートリッジシェルに収まりません)。ICやコンデンサのリードの処理は通常通りで構いません。
4. タクトスイッチと電池ホルダをハンダ付けします。標準では、タクトスイッチは裏面、電池ホルダは表面に配置しますが、逆の面に配置することもできますので、お好みで配置してください。
5. ショートや部品の付け間違いがないことを念入りに確認したうえで、MSX実機に挿して動作を確認します。似非RAMディスクとして使わない場合でも、動作確認にはMGINSTを使うのが簡単です。

## 準備 (似非RAMディスクとして使う場合)
1. 似非インストーラー(MGINST.COM)とカーネルセーバー(KSAVER.COM)を入手します([似非職人工房・非公認出張所(似非なページ)](http://www.big.or.jp/~saibara/msx/ese/index-j.html)よりLHA形式のアーカイブをダウンロードすることができます。また、ZIP形式にアーカイブしなおした[MGINST215.zip](https://github.com/goriponsoft/ESE2RAM-Cartridge-74670/blob/main/MGINST215.zip)と[KSAVER105.zip](https://github.com/goriponsoft/ESE2RAM-Cartridge-74670/blob/main/KSAVER105.zip)も、こちらで用意してあります。)
2. 何らかのMSXで起動可能なストレージ(通常はフロッピーディスク)に上記ツールを展開したものと、MSX-DOSのシステムファイル(MSXDOS.SYS/COMMAND.COM)をコピーします。MSX-DOS2カーネル利用の場合は、加えてMSX-DOS2のシステムファイル(MSXDOS2.SYS/COMMAND2.COM)をコピーしておくと、似非RAMインストール時に自動的にコピーされ、MSX-DOS2で起動することができるようになります。
3. MSX実機に似非²RAMカートリッジを挿し、タクトスイッチを押したまま電源を入れ、手順2で作成したストレージからMSX-DOS(またはMSX-DOS2)を起動します。
4. KSAVER.COMを使用し、MSX本体からMSX-DOSまたはMSX-DOS2のカーネルをファイルに保存します(詳細はKSAVERの付属ドキュメントを参照)。
5. MGINST.COMを使用し、手順4で保存したカーネルのファイルを指定して似非RAMカーネルをインストールします(詳細はMGINSTの付属ドキュメントを参照)。
6. リセットし似非RAMディスクから起動することを確認します。

手順4で保存したカーネルファイルは不要ですので、削除してしまっても構いません。残しておくと、似非RAMディスクの再インストール時に手順を省略できます。

手順5でエラーが出る場合は、部品のハンダ付け不良の可能性が高いので、基板をチェックしてみてください。

## 使い方 (メガROMソフトウェアを動かす場合)
使用した部品の機能の関係で、当カートリッジでは、セグメント番号の初期値がASCIIマッパーと異なっているため、プログラムによるレジスタの初期化が必須となっています。似非RAMディスクやゲームを含む、ほとんどのメガROMソフトウェアでは適切に初期化が行われているので問題ありませんが、初期化を怠っていたり、セグメント初期値が特定の値であることを期待しているソフトウェアは動作しない場合があります。

当カートリッジの起動直後もしくはリセット直後のバンクは以下のようになっています。

|バンクアドレス|レジスタアドレス|セグメント番号|
|:--|:--|--:|
|4000h-5FFFh|6000h-67FFh|0|
|6000h-7FFFh|6800h-6FFFh|0|
|8000h-9FFFh|7000h-77FFh|0|
|A000h-BFFFh|7800h-7FFFh|0|

この状態からレジスタに値を書き込むと、書き込んだレジスタは書き込んだ値に、書き込まれていないレジスタは不定値に切り替わります。

例えば6000hに0を書き込んだ場合は以下のようになります。

|バンクアドレス|セグメント番号|
|:--|--:|
|4000h-5FFFh|0|
|6000h-7FFFh|不定|
|8000h-9FFFh|不定|
|A000h-BFFFh|不定|

このため、当カートリッジで自作メガROMソフトウェアを動作させる場合は、INITエントリのできるだけ早い段階で、実行中のアドレスを含むバンクのレジスタに0を書き込んで初期化する必要があります。実行中のアドレスを含まないバンクのレジスタに先に書き込んでしまうと、実行中のプログラムが不定のバンクに切り替わり、ほとんどの場合は暴走します。また、書き込まれなかったレジスタの値は不定ですので、必要であれば初期化を行ってください。

通常はセグメント#0に以下のコードを配置し、ROMヘッダのINITエントリより4000h～5FFFhバンクのコードとして呼び出せば、問題なく初期化できます。
```
	xor		a
	ld		(6000h),a
	ld		(6800h),a
	ld		(7000h),a
	ld		(7800h),a
```

## 互換性情報
動作確認済のハードウェア(順不同)について

ご報告いただいたものは順次追加していきます

### 動作不良が確認されている機種と症状

- ビクター HC-90 および HC-95 (MSX2) : RAMから読み出されたデータが壊れるため正常動作しない
- 東芝 HX-E601 (拡張スロット) : 認識されず起動しない

### 正常動作が確認されている機種

- パナソニック FS-A1ST
- ソニー HB-F1XV
- 三菱 ML-G30model1 および ML-G30model2
- ヤマハ YIS503 および CX5F
- ヤマハ YIS604/128 および CX7M/128
- 三洋 WAVY70FD および WAVY70FD2
- 東芝 HX-31
- 三菱 ML-8000
- ゼネラル PCT-50 および PCT-55
- ソニー HB-F500
