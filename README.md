# ToPu_ViewSmooth

[![Blender](https://img.shields.io/badge/Blender-4.2%2B-F5792A?logo=blender&logoColor=white)](https://www.blender.org/)
[![License](https://img.shields.io/badge/License-GPL--3.0--or--later-blue.svg)](#ライセンスとクレジット)

**ビューを基準に選択辺を整えます。**  
Align the selected edges based on the view.

選択した開いた辺ループを、ビュー上の2Dカーブとして整えるBlenderアドオンです。各ループの両端と、選択頂点のビュー方向の奥行きを保ちながら、画面上の横・縦方向に形状を調整できます。

## 対応環境

- Blender 4.2以降
- 表示言語：日本語 / English。アドオンプリファレンスの概要説明は両言語を併記
- 対象：メッシュ編集モードの、3頂点以上で分岐のない開いた辺ループ

## ダウンロード

配布用ZIPは [Releases](https://github.com/http4211/ToPu_ViewSmooth/releases) からダウンロードしてください。

## インストール

1. ReleasesからアドオンのZIPファイルをダウンロードします。
2. ZIPを展開せず、Blenderのウィンドウへドラッグ＆ドロップしてインストールします。
3. ドラッグ＆ドロップを使わない場合は、`編集 > プリファレンス > アドオン` のメニューから `ディスクからインストール` を選び、ZIPを指定します。
4. アドオン一覧で **ToPu_ViewSmooth** を有効にします。

`topu_view_curve`フォルダーを含む配布用ZIPを使用する、従来形式のアドオンです。

## 場所

**3Dビュー > 編集モード > 右クリック > ToPu Tools > ViewSmooth**

初期ショートカットは **Ctrl＋Alt＋C** です。アドオンプリファレンスから変更できます。

| ほかの起動場所 | 操作 |
| --- | --- |
| 左ツールバー（Tキー） | **ToPu_ViewSmooth**を選び、ビュー内を左クリック |
| 編集モードの「辺」メニュー | **ToPu_ViewSmooth**を選択 |
| F3検索 | **ToPu_ViewSmooth**を検索して実行 |

既存の**ToPu Tools**メニューが利用できる場合は、その中にViewSmoothを追加します。`ToPuTools`のように空白がない表示名も認識します。利用できるメニューがない場合は、このアドオンがToPu Toolsを表示します。

## 主な機能

### ビューを基準に整形

- 平行投影・透視投影に対応
- 選択頂点の奥行きと、各ループの両端を保持
- 複数の開いた辺ループ・複数オブジェクトを同時に処理
- 横方向のみ・縦方向のみの移動にも対応
- 開始時の座標から計算するため、操作中の変形が累積しない

### カーブ量とスムーズ量

**マウスの左右移動でスムーズ量、ホイールでカーブ量**を調整します。どちらも独立して **−1000%〜1000%** の範囲で設定できます。

| 設定 | 初期値 | 効果 |
| --- | --- | --- |
| スムーズ量 / Smoothness | 65% | 正の値で曲がりやガタつきを抑えます。0%で平滑化なし、負の値で元の曲がりや凹凸を強調します。 |
| カーブ量 / Curve Amount | 100% | 両端を結ぶ直線からの膨らみを調整します。0%で直線、100%でスムーズ適用後のカーブ、−100%で膨らむ向きが反転します。 |

HUDはパーセント表示です。プロパティの値では、`1.0`が`100%`に相当します。**スムーズ量0%・カーブ量100%で開始時の形に戻ります。**

カーブ量0%で直線になるのは、横＋縦で調整する場合です。横／縦の片方向に制限した場合は、許された方向への移動だけを適用します。

### 編集モードのミラー

編集モードの**X／Y／Z位置ミラー**に対応し、複数軸を同時に使用できます。片側のループを調整すると、実メッシュ内の反対側にある対応頂点へ、反転した移動量を適用します。

ミラーの基準はオブジェクトのローカル座標と原点です。**選択側の奥行きは固定しますが、斜めのビューではミラー側の奥行きが変化する場合があります。** 両側を選択した場合は、各側を独立したカーブとして処理します。

### コンパクトなHUD

画面下部中央に、**カーブ量とスムーズ量を1行**で表示します。半透明グレーのパネル内に2つの項目を並べ、それぞれの左側に操作ヒントの **Wheel / マウス移動** を枠付きで表示します。カーブ量は青、スムーズ量は紫をアクセントにし、直前に調整した項目の背景と左端を強調します。文字サイズはBlenderのUIスケールに従い、狭いビューでは収まるように縮小します。

## 基本的な使い方

1. メッシュの編集モードに入り、辺選択モードにします。
2. 整えたい**3頂点以上の開いた辺ループ**を選択します。離れた複数のループも同時に選択できます。
3. 整える基準にしたい方向へビューを合わせます。
4. **右クリック > ToPu Tools > ViewSmooth**、または **Ctrl＋Alt＋C** で起動します。
5. マウスの左右移動とホイールで形を調整します。
6. **左クリックで確定、右クリックで開始時の形へ戻してキャンセル**します。

確定後は **F9** から、スムーズ量・カーブ量・移動方向を再調整できます。

ツールバーから使う場合は、先に標準の選択ツールで辺を選択してください。四分割ビューでは、基準にしたいビュー内へマウスを置き、ショートカットから開始します。

## 操作方法

| 操作 | 内容 |
| --- | --- |
| マウスを左右に移動 | スムーズ量を調整 |
| ホイール | カーブ量を調整。1段で10パーセントポイント |
| 左クリック | 確定 |
| 右クリック | 開始時の頂点位置へ戻してキャンセル |
| 3Dマウスの移動・回転入力／中ボタン／トラックパッド | ビューの移動・回転・ズーム |

実行中の調整はマウス移動とホイールで行います。数値や移動方向を直接指定したい場合は、起動前のツール設定・アドオンプリファレンス、または確定後のF9を使用してください。

**変形の方向と奥行きは、実行開始時のビューが基準です。** ビューを回転しても基準は変わりません。新しい方向を基準にする場合は、一度確定またはキャンセルして起動し直してください。F9も開始時のビューを使用します。

ビュー操作後は、次のマウス移動で位置の基準を取り直します。ホイールはカーブ量の調整に使用し、3Dマウスの任意のボタン入力や別のメッシュ編集操作は通しません。キャンセルで戻すのは頂点位置で、操作中に変更したビュー方向はそのままです。

## オプション

**プリファレンス > アドオン > ToPu_ViewSmooth** から、次の項目を設定できます。

- 起動ショートカットのキーと修飾キー
- 開始時のスムーズ量・カーブ量。負の値も設定可能
- 移動方向：横＋縦 / 横方向のみ / 縦方向のみ

ショートカットを変更したら、必要に応じてプリファレンスを保存してください。左ツールバーのツール設定で値を明示的に指定した場合は、その値を使用します。

## 処理対象と制限

- 対象は、選択辺でつながった**3頂点以上・端点2つ・分岐なし**の列です。閉じたループ、分岐した選択、1辺だけの選択は除外します。有効なループが混在していれば、そのループは処理します。
- 面の中にある辺も対象です。選択していない辺は分岐の判定に含めません。
- 頂点を等間隔に並べ直す機能ではありません。頂点・辺・面の追加や削除も行いません。
- ミラーは位置による照合です。**トポロジーミラーによる対応付けには非対応**で、有効にしていても位置で照合します。対応先がない・一意に決まらない・非表示の場合は、その頂点への反映を省略します。
- 正常に投影できない列や、異なる変換行列のオブジェクトが共有するメッシュなどは除外します。

詳しい条件は配布用ZIP内の`README.md`を参照してください。Blender本体のGUI、3Dマウス実機、他アドオンとの組み合わせについては、現在の構成での動作確認は未実施です。

## ライセンスとクレジット

**GNU General Public License v3.0 or later（GPL-3.0-or-later）** の下で配布します。ライセンス本文は、配布用ZIP内の`LICENSE`を参照してください。

- 作者：[http4211](https://github.com/http4211)
- リポジトリ：[http4211/ToPu_ViewSmooth](https://github.com/http4211/ToPu_ViewSmooth)
- Copyright (C) 2026 http4211

不具合報告や要望は [Issues](https://github.com/http4211/ToPu_ViewSmooth/issues) へお願いします。

---

<details>
<summary><strong>English</strong></summary>

## Overview

**ToPu_ViewSmooth** reshapes selected open edge chains as 2D curves in Blender's Mesh Edit Mode. It keeps each chain's endpoints and the selected vertices' depth in the starting view while adjusting their horizontal and vertical positions.

Move the mouse horizontally to adjust **Smoothness**, and use the wheel to adjust **Curve Amount**. Both parameters support negative values.

## Requirements

- Blender 4.2 or later
- Mesh Edit Mode; open, unbranched edge chains with at least 3 vertices
- Japanese / English UI; the add-on preferences overview is always shown in both languages

## Download and installation

1. Download the add-on ZIP from [Releases](https://github.com/http4211/ToPu_ViewSmooth/releases).
2. Keep the ZIP compressed, then drag and drop it into Blender to install it.
3. Alternatively, open `Edit > Preferences > Add-ons`, choose `Install from Disk` from the menu, and select the ZIP.
4. Enable **ToPu_ViewSmooth** in the add-on list.

Use the packaged ZIP containing the `topu_view_curve` folder. This is a legacy-format add-on.

## Location

**3D View > Edit Mode > Right-click > ToPu Tools > ViewSmooth**

Default shortcut: **Ctrl + Alt + C**, configurable in the add-on preferences.

You can also launch **ToPu_ViewSmooth** from the left toolbar, the Edge menu, or F3 search. The ViewSmooth item joins an available ToPu Tools menu; otherwise, the add-on displays its own menu.

## Main features

- Process multiple separate open chains and multiple objects together.
- Support orthographic and perspective views while keeping chain endpoints and selected-vertex view depth.
- Adjust Smoothness and Curve Amount independently from **−1000% to 1000%**.
- Restrict movement to the horizontal or vertical direction through settings.
- Follow mesh X/Y/Z position mirror settings, including multiple axes.
- Show Curve Amount and Smoothness in one row inside a translucent gray panel. Separate Wheel / Mouse Move hint boxes and blue / purple accents identify each control; the last adjusted field is highlighted.
- Recalculate from the starting coordinates so adjustments do not accumulate.

| Parameter | Default | Effect |
| --- | --- | --- |
| Smoothness | 65% | Positive values smooth bends and irregularities. Zero applies no smoothing. Negative values reverse the smoothing displacement to emphasize the original bends. |
| Curve Amount | 100% | Controls the offset from the line between the endpoints. Zero makes the chain straight; 100% keeps the smoothed curve; negative values reverse its bend direction. |

The HUD uses percentages; a property value of `1.0` corresponds to `100%`. **Smoothness 0% and Curve Amount 100% restore the starting shape.** A zero Curve Amount makes the chain straight when both screen directions are enabled; an axis restriction applies only the permitted movement.

## Quick start

1. Enter Mesh Edit Mode and select one or more valid open edge chains.
2. Orient the view to the direction you want to use for the adjustment.
3. Run **ToPu Tools > ViewSmooth** or press **Ctrl + Alt + C**.
4. Adjust the shape using mouse movement and the wheel.
5. **Left-click to confirm, or right-click to cancel and restore the starting coordinates.**

After confirming, use **F9** to adjust the parameters again. Both live adjustment and F9 use the view captured at the start.

## Essential controls

| Input | Action |
| --- | --- |
| Horizontal mouse movement | Adjust Smoothness |
| Mouse wheel | Adjust Curve Amount; 10 percentage points per step |
| Left-click | Confirm |
| Right-click | Cancel and restore the starting vertex positions |
| 3D mouse motion / middle mouse button / trackpad | Navigate the view |

Live adjustment uses mouse movement and the wheel. Set exact values and screen movement restrictions in the tool settings or add-on preferences before starting, or in F9 after confirming.

Navigating the view does not change the adjustment basis. To use another view direction, finish or cancel and start again. Arbitrary 3D mouse button commands and other mesh edits are consumed while the adjustment is active. Canceling restores vertex positions, but keeps any view navigation.

## Options and limitations

In **Preferences > Add-ons > ToPu_ViewSmooth**, configure the launch shortcut, initial Smoothness, Curve Amount, and screen movement direction. Save preferences when needed to retain shortcut changes.

Closed loops, branched selections, and single edges are skipped. Unselected edges do not count as branches. This tool does not redistribute vertices at equal intervals or add/remove mesh elements.

Mirroring uses existing vertex positions in object-local coordinates, relative to the object origin. **Topology-based mirror matching is not supported.** Missing, ambiguous, or hidden destinations are skipped. The selected side keeps its view depth; the mirrored side may change depth in an oblique view. When both sides are selected, each chain is processed independently.

The current build has not been verified in Blender's GUI, with a physical 3D mouse, or in combination with other add-ons.

## License and credits

Distributed under **GNU General Public License v3.0 or later (GPL-3.0-or-later)**. The full license text is included as `LICENSE` in the add-on ZIP.

- Author: [http4211](https://github.com/http4211)
- Repository: [http4211/ToPu_ViewSmooth](https://github.com/http4211/ToPu_ViewSmooth)
- Copyright (C) 2026 http4211

Please report bugs and feature requests through [Issues](https://github.com/http4211/ToPu_ViewSmooth/issues).

</details>
