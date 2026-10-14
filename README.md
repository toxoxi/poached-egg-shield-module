# poached-eggs / goforty 配列

Mac・US配列用。ZMK v0.3.0。公式定義の50キーに合わせた設定です。

## 最下段（各行は左から右）

- 左: MO(3) / 未割当 / Alt / Command / 英数(L1長押し) / Space / 未割当
- 右: Enter / 未割当 / かな(L2長押し) / Backspace / Escape / 未割当 / 未割当

英数・かなはLANG2・LANG1を送信します。長押し判定は200ms、balancedです。gofortyの元のタイミング設定はPDFから分からないため、打鍵感は実機で調整してください。

## レイヤー

0. Base: 文字配列。右Shiftは追加せず、右手3段目の末尾は元のPDF同様に未割当。
1. Symbols: 元の数字・記号配列。中央列のSpace/Ctrl+Wは削除。
2. Navigation: 元のファンクション・矢印・括弧配列。Macro 0はCtrl+Alt+Left、Macro 1はCtrl+Alt+Rightの同時押しを1回送信。
3. Shortcuts: 元のショートカット・テンキー配列。中央列のShift+Command+3は削除。右下はCtrl+Shift+Command+4。Vの位置はShift+Command+4。右端のEnterは短押しEnter・長押しCommand、Escは短押しEsc・長押しShift。
4. System: 新規の管理専用レイヤー。旧レイヤー4〜6は移植していません。

## BluetoothとStudio

左下MO(3)を押したまま、右最下段の右から2番目を長押しするとSystemへ入ります。

- 左上段の左から1〜5番目: Bluetoothプロファイル1〜5を選択。
- 左中段の一番左（通常Ctrl）: Studio Unlock。
- 2つのレイヤーキーを離すとBaseに戻ります。

ペアリング消去キーは誤操作防止のため割り当てていません。

## ビルドと書き込み

設定: `config/poached_eggs.keymap`

GitHub ActionsのBuildワークフロー成功後、firmwareアーティファクトをダウンロードします。左右のUF2名にleft/rightが含まれることを確認してください。

1. 左側をUSB接続し、リセットスイッチを素早く2回押します。
2. 表示されたXIAO-SENSEドライブへleftのUF2をコピーします。
3. 右側も同様にrightのUF2を書き込みます。
4. 電源を入れ、Macで接続・入力確認します。

既にZMK Studioで保存した設定があると、UF2を書き換えても保存済み設定が優先されることがあります。その場合はStudioでキーマップをファームウェア初期値へ戻してください。ペアリング全消去用ファームウェアは通常不要です。

## 実機確認

- 英数/かなの短押し、押しながらの数字・矢印。
- レイヤー2のCtrl+Alt+左右。
- MO(3)+右下の範囲選択スクリーンショット。選択後、画像を貼り付けて確認。
- Space/Enter/Backspace/Escapeの位置。

ファームウェアのビルド確認と、実機上の入力動作確認は別です。実機確認は書き込み後に行ってください。

公式: https://site.omuken.me/poached-eggs/user-guide/
ベース: https://github.com/omwegg/poached-egg-shield-module
ベースcommit: 92d67c950a6f8579f6f097341c0454bcfce52a9c
