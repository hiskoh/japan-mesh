# japan-mesh

日本全国分のメッシュデータを政府統計の総合窓口（e-Stat）のデータをもとに整備しました。

<img height="300" alt="image" src="https://github.com/hiskoh/japan-mesh/assets/13606213/8b55cef1-c702-4f18-b033-34a28f1744a1">

<img height="300" alt="image" src="https://github.com/hiskoh/japan-mesh/assets/13606213/0701d262-987e-49da-979d-2ce927b96d02">

## データ公開先
ファイル容量が大きくGithubへのアップロードができないため、下記のBOXフォルダにて公開しています。

https://app.box.com/s/6g83k1nwam6m1i6iu8ykm9mwhk6dm1ns

* japan-mesh-4th ：3次メッシュ（1kmメッシュ）世界測地系緯度経度。
* japan-mesh-4th ：4次メッシュ（500mメッシュ）世界測地系緯度経度。
* japan-mesh-5th ：5次メッシュ（250mメッシュ）世界測地系緯度経度。

※それぞれGeojson, GeoPackage(gpkg), FlatGeobuf(fgb), Shapefile(shp) の4種類のデータ形式で公開しています。

## データ出典
これらのメッシュは、政府統計の総合窓口（e-Stat）で公開されている「境界データ」をもとに作成しています。　

政府統計の総合窓口（e-Stat）

https://www.e-stat.go.jp/gis/statmap-search

e-Statの利用規約等に沿ってご使用ください。

https://www.e-stat.go.jp/terms-of-use

https://www.e-stat.go.jp/help/data-definition-information/download

## データの整備方法
1. e-Statで公開されている「境界データ」のすべてをダウンロード（ZIPファイルがダウンロードされる。今回は世界測地系緯度経度・GMLをダウンロード）

3. 上記ZIPファイルをすべて展開。ただし手作業だと時間がかかるので、下記Pythonコードで一気に展開。
```
import zipfile, glob

#zipfile一覧を取得
fs = glob.glob('C:\\Users\\hoge\\mesh\\ori\\*')

#zipfile一覧を順次解凍
for f in fs:
    zip = zipfile.ZipFile(f)
    zip.extractall('C:\\Users\\hoge\\mesh\\new\\')
    zip.close()
```

3. QGIS「ベクターレイヤをマージ」機能で先ほど展開したフォルダのパスを指定
   
<img width="500" alt="image" src="https://github.com/hiskoh/japan-mesh/assets/13606213/46b6e41b-46c6-4e9e-bb35-61180d8c4507">

## 備考

・プライベート＆業務で使用したくて整備しました。もしデータ不備がありましたらissue上げてもらえると嬉しいです。

・本データの正確性や完全性についての責任を負いませんので、ご自身でデータを検証しながらお使いください。

**GISでいろんなデータをマッピングしましょう！**
