# 似非²RAMカートリッジ
[English README is here](https://github.com/goriponsoft/ESE2RAM-Cartridge-74670/blob/main/README-en.md)

これは、汎用ロジックICにより似非RAMを構築したMSX用カートリッジ(命名:似非・似非RAMまたは似非²RAM)です。
ごりぽんハードウェア(同人サークル・ごりぽんソフトウェアのハードウェア部門)により作成されました。

クリエイティブ・コモンズライセンス(CC-BY-NC)で公開されています。

X(旧Twitter): @goriponsoft

## 似非RAMDisk(似非RAM)とは？

[同人サークル・似非職人工房](http://www.hat.hi-ho.ne.jp/tujikawa/ese/)のつじかわ氏が考案した、ストレージなどとして使えるMSX用の汎用バックアップRAMカートリッジです。

通常は、ゲームのメガROMカートリッジを改造し、ROMをRAMに置き換えることで制作します。MGINSTコマンドによりDOSカーネルをインストールしてSSDのようなストレージとして利用したり(似非RAMDisk)、メガROMのイメージを読み込ませて動作させたりすることができます。

もともとストレージとしての使用を前提に考案されたため、カートリッジ自体も「似非RAMDisk」と呼ぶほうが一般的です。

なお、所有していないゲームのイメージを読み込ませて利用することは違法行為です。通常は似非RAMDiskの他、似非RAMに改造することで使用できなくなる改造元ゲームカートリッジのイメージ(改造前にファイルに書き出しておく必要あり)、フリーウェア、自作ROMゲーム、などを動作させるのに使用します。

似非RAMDiskについての詳細は、[似非職人工房の似非RAMDiskのページ](http://www.hat.hi-ho.ne.jp/tujikawa/ese/eseram.html)を参照してください。

## 似非²RAM(似非・似非RAM)とは？

近年MSXゲームの入手自体が難しくなり、貴重になってしまったメガROMカートリッジを潰して似非RAMにするのはかなり躊躇われる状況でした。そこで、普通に入手できる(ちょっと入手が面倒なものもありますが)汎用ロジックICを使い、メガROMコントローラーと同等の回路を構築し、似非RAMとして組み上げたのがこのカートリッジです。

似非RAMでありながら、メガROMコントローラを使用していない「似て非なる似非RAM」ということで「似非・似非RAM」、転じて「似非の2乗」で「似非²RAM」と命名しました。英語表記は「ESE-ESE-RAM」または「ESE2-RAM」です。

## 部品表
|部品番号|内容|数量|
|:--|:--|--:|
|BT1|CR2032電池ホルダ "CH29-2032LF"/"CH28-2032LF(TR)"/"CH004-2032LF"/"CH004-2032LF"のいずれか|1|
|C1-C8|セラミックコンデンサ 0.1μF・50V|8|
|C9|電解コンデンサ 10μF・16V|1|
|D1-D2|ダイオード "1N4148"|2|
|IC1-IC2|SRAM(628512タイプ・512K×8) DIP-32 "AS6C4008"など|2|
|R1-R4|抵抗 1/4W・10KΩ|4|
|RN1|集合抵抗 8素子・10KΩ|1|
|S1|6×6mm タクトスイッチ "DTS-63N-V"|1|
|U1-U2|汎用ロジックIC "74HC670"|2|
|U3|汎用ロジックIC "74HC138"|1|
|U4|汎用ロジックIC "74HC00"|1|
|U5|汎用ロジックIC "74HC32"|1|
|-|CR2032電池|1|

## 組み立て方
基板の実装面積の関係で、抵抗やコンデンサなどの部品が裏面(ハンダ面)に配置されているため、組み立てには注意が必要です。

1. 基板を裏返して(コネクタの傍に「Front」と書かれている側が表面です)、シルク印刷を参考に、ダイオード、抵抗、セラミックコンデンサ、電解コンデンサ、集合抵抗、の順で部品を配置して表側(部品面)からハンダ付けしてください。ハンダを盛りすぎると、ICと基板の間に隙間ができるので、ハンダの量は控えめにしてハンダ付けしてください。
2. ハンダ付けしたら、表面に余ったリードを切断します。リードが余分に残っていると、やはりICと基板の間に隙間ができるので、こちらもできるだけ短くなるように切断してください。
3. 基板を表に戻し、ICとCR2032電池ホルダを配置し、通常通り裏面(ハンダ面)からハンダ付けしていきます。ICやホルダのリードはそのままで構いません。
4. タクトスイッチをハンダ付けします。標準では裏面に配置しますが、表面に配置することもできますので、お好みで配置してください。

## 準備(似非RAMDiskとして使う場合)
1. 似非インストーラー(MGINST.COM)とカーネルセーバー(KSAVER.COM)を入手します([似非職人工房・非公認出張所(似非なページ)](http://www.big.or.jp/~saibara/msx/ese/index-j.html)よりダウンロードすることができます)。
2. 何らかのMSXで起動可能なストレージ(通常はフロッピーディスク)に上記ツールを展開したものと、MSX-DOSのシステムファイル(MSXDOS.SYS/COMMAND.COM)をコピーします。MSX-DOS2カーネル利用の場合は、加えてMSX-DOS2のシステムファイル(MSXDOS2.SYS/COMMAND2.COM)をコピーしておくと、似非RAMインストール時に自動的にコピーされ、MSX-DOS2で起動することができるようになります。
3. 手順2で作成したストレージからMSX-DOS(またはMSX-DOS2)を起動します。
4. KSAVER.COMを使用し、MSX本体からMSX-DOSまたはMSX-DOS2のカーネルをファイルに保存します(詳細はKSAVERの付属ドキュメントを参照)。
5. MGINST.COMを使用し、手順4で保存したカーネルのファイルを指定して似非RAMカーネルをインストールします(詳細はMGINSTの付属ドキュメントを参照)。
6. リセットし似非RAMDiskから起動することを確認します。

手順4で保存したカーネルファイルは不要ですので、削除してしまっても構いません。残しておくと、似非RAMDiskの再インストール時に手順を省略できます。

手順5でエラーが出る場合は、部品のハンダ付け不良の可能性が高いので、基板をチェックしてみてください。