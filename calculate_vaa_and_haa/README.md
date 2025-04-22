# Estimate VAA & HAA from Statcast Data

## 概要
- Statcastで取得できるデータから、ボールのVAA（Vertical Approach Angle、垂直アプローチ角度）・HAA（Horizontal Approach Angle、水平アプローチ角度）の推定値を計算しています。
- 計算内容は以下のサイトの内容に準拠しています。
    - [VAA : A Visualized Primer on Vertical Approach Angle (VAA)](https://blogs.fangraphs.com/a-visualized-primer-on-vertical-approach-angle-vaa/s)
    - [HAA : A Visual Primer on Horizontal Approach Angle (HAA)](https://blogs.fangraphs.com/a-visual-primer-on-horizontal-approach-angle-haa/)

## 計算内容
本ファイルでは、以下の流れで推定値の計算を実施しています。
### 1. MLBのStatcastデータを取得
- 例として、pybaseballを利用して、指定期間のStatcastデータを取得しています。
- Statcastを使用しない方法（フォルダ[extract_savant_data](../extract_savant_data/)の内容）でも、計算に必要なデータを取得することは可能です。
### 2. ボールのVAA・HAAの計算
- 前述の計算方法に沿って、ボールのVAA・HAAを計算・追加します。
- 追加されるデータは以下の通りです。
    - vaa : ボールのVAA
    - haa : ボールのHAA

## 利用言語・環境等
- 言語はPythonで記述しています。
- ファイルはJupyter Notebook形式（.ipynb）にて保存しています。

## 使い方
- Google Colab等、Jupyter Notebookをご利用可能であれば、順次コードを実行するだけで結果を得ることができます（検証済）。
- .pyファイルとして実行される際は、必要に応じて修正の上ご利用ください。