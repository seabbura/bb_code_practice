# Estimate Arm Angle from Statcast Data

## 概要
- Statcastで取得できるデータから、リリース角度（Arm Angle）の推定値を計算しています。
- 計算方法は[こちらのサイト](https://web.archive.org/web/20230123183755/https://www.rundownbaseball.com/project/calculating-arm-angles-using-statcast-data/#:~:text=rubber%20at%20extension,aka%20shoulder%29%20is)の内容に準拠しています。
- Arm AngleはSavantのMajor League Searchから取得可能ですが、Minor League SearchおよびGamefeedには値がありません。このため推定を行うものです。

## 計算内容
本ファイルでは、以下の流れで推定値の計算を実施しています。
### 1. MiLB（Minor League）のStatcastデータを取得
- 例として、MiLBの日付を指定し、指定期間のStatcastデータを取得しています。
- フォルダ[extract_savant_data](../extract_savant_data/)内にある[savant_extract_milb_data.ipynb](../extract_savant_data/savant_extract_milb_data.ipynb)と内容は同じです。
### 2. 投手の身長データの取得
- 取得したデータの内容に基づいてStats APIを参照し、各投手の身長を取得します。
    - 身長はinch単位に変換しています。
### 3. Arm Angle推定値の計算
- Statcastデータ（特にリリース位置）・投手の身長から、Arm Angleの推定値を計算します。
    - それぞれの値はinch単位に揃えています。
- Arm Angleの計算に必要となる肩のx位置（水平位置）・z位置（垂直位置）は以下のように仮定しています。
    - x位置 : 0（プレートの中央）とする。
    - z位置 : 各投手の身長の70%とする。
- 本計算で追加されるデータは以下の通りです。
    - height : 投手の身長（インチ単位）
    - release_pos_x_inches : 投手の水平リリース位置（インチ単位、絶対値）
    - release_pos_z_inches : 投手の垂直リリース位置
    - sld_z : 投手の垂直肩位置の推定値（身長の70%で計算した値）
    - arm_angle_estimate : リリース角度の推定値
> [!WARNING]  
> - 本方式で取得できる値はあくまで推定値であり、正確な値ではありません（Major League Search(2024)との相関係数は約0.78でした）。
> - 上記の計算方式のため、特にリリース位置がプレートの中央近くにある投手は、極端な値が出ることがあります。

## 利用言語・環境等
- 言語はPythonで記述しています。
- ファイルはJupiter Notebook形式（.ipynb）にて保存しています。

## 使い方
- Google Colab等、Jupiter Notebookをご利用可能であれば、順次コードを実行するだけで結果を得ることができます（検証済）。
- .pyファイルとして実行される際は、必要に応じて修正の上ご利用ください。