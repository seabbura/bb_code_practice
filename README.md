# Baseball Code Practice
## 概要
- 野球のデータ取得・計算のためのコード集です。
- 主にMLB（Statcast）のデータに関する処理を取り扱っています。
- 追加・修正・削除は随時行う予定です。

## ラインナップ
### extract_savant_data
- （pybaseballなしで）Statcastのコードを取得します。
- MLB版・MiLB版の2ファイルがあります。

### extract_gamefeed_data
- Savantの試合データ（Gamefeedデータ）を取得します。
- データ取得に加え、いくつかの計算およびフィールドの追加を行っています。

### calculate_vaa_and_haa
- Statcastのデータから、垂直アプローチ角度（VAA）・水平アプローチ角度（HAA）を計算しています。

### calculate_observed_movement
- Statcastのデータから、ボールの動作角度（Observed Movement）・回転効率（Spin Efficiency）を計算しています。

### calculate_arm_angle_estimate
- Statcastのデータから、投手のリリース角度（Arm Angle）を計算しています。

## 言語・ファイル形式等
- 言語はすべてPythonで記述しています。
- ファイルはすべてJupiter Notebook形式（.ipynb）形式で作成しています。
    - Google Colab等、Jupiter Notebookをご利用可能であれば、順次コードを実行するだけで結果を得ることができます（検証済）。
    - .pyファイルでご利用の場合は、適宜修正してお使いください。