# Savant Observed Movement Estimate

## 概要
- Statcastで取得できるデータから、ボールの動作角度（Observed Movement Angle）・回転効率（Spin Efficiency）の推定値を計算しています。
- 計算内容は[こちらのサイト](https://www.kaggle.com/code/s903124/observed-vs-inferred-spin-axis)に準拠しています。
> [!WARNING]  
> - 本方式で回転効率の推定値も取得できますが、実際のSavantデータと比較すると乖離が大きいこと、また1を超える値が出ることもあるため、利用は非推奨です。

## 計算内容
本ファイルでは、以下の流れで推定値の計算を実施しています。
### 1. MLBのStatcastデータを取得
- 例として、pybaseballを利用して、指定期間のStatcastデータを取得しています。
- Statcastを使用しない方法（フォルダ[extract_savant_data](../extract_savant_data/)の内容）でも、計算に必要なデータを取得することは可能です。
### 2. ボールの動作角度・回転効率の計算
- 前述の計算方法に沿って、ボールの動作角度・回転効率のデータを計算・追加します。
- 追加されるデータは以下の通りです。
    - phi : 動作角度
    - spin_eff : 回転効率

## 利用言語・環境等
- 言語はPythonで記述しています。
- ファイルはJupiter Notebook形式（.ipynb）にて保存しています。

## 使い方
- Google Colab等、Jupiter Notebookをご利用可能であれば、順次コードを実行するだけで結果を得ることができます（検証済）。
- .pyファイルとして実行される際は、必要に応じて修正の上ご利用ください。