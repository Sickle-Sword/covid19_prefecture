# covid19_prefecture
各都道府県からコロナウイルス感染者のデータを取得し，クリーニングしています

## 使い方

* Rユーザーの方
データ統合.Rのスクリプトを実行すれば，マージされたデータが入手できます。  
ただし，データソースのURLがコロコロ変更される県もあるようなので，
動かないときは修正をお待ちください…  
（更新はゆっくりになるかもしれません）

* Rユーザーでない方  
csvファイルを直接ダウンロードできます。  
data/covid19_merge.csvをダウンロードしてください。

## 注意点

都道府県によって使えないデータ列もあるので注意です。   
「居住地」は北海道の場合は振興局単位（札幌市は除く），それ以外の都道府県では市町村単位です。


## データクリーニング方針

### 公表日
* 患者と紐づけられた日付情報が1つの場合はそれを用いる
* 「公表日」「発症日」のように複数ある場合は「公表日」を用いる

### 性別
* 「男性」「女性」以外は欠損値とする

### 年代
* 10歳未満は「0代」とする
* 90歳以上の場合は「90代」カテゴリに含める
* 調査中等の場合は欠損値とする

### 居住地
* 基本的に市区町村単位でコーディングする
* 北海道は札幌市と振興局でコーディング
* 福岡県は市と郡を用いる 
* 都道府県外であることがわかる場合は「県外」とする
* 「調査中」や県内であることはわかるが市町村が判然としない場合は欠損値とする
