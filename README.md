# copc-format-nagasaki-point-cloud-data

## Public Website
- Ctrlを押しながらドラッグで回転できる  
- 色はデフォルトでElevationになっているのでパネルからRGBに変更すると実際の色で表示できる  
https://viewer.copc.io/?copc=https://xs489works.xsrv.jp/copc-data/open_nagasaki/01ke9821_translated.copc.laz

## COPC（Cloud Optimized Point Cloud）の生成方法
- [pdal 2.5.2](https://pdal.io/en/latest/)

```
# OSGeo4W Shellを起動
# メタデータの確認
pdal info --metadata 01ke9821_org.las

# 座標参照系の付与
pdal translate -i 01ke9821_org.las -o 01ke9821_translated.las --writers.las.a_srs="EPSG:6669"

# メタデータの確認
pdal info --metadata 01ke9821_translated.las

# COPCへの変換
pdal translate -i 01ke9821_translated.las -o 01ke9821_translated.copc.laz --writers.copc.forward=all
```

## COPC ViewerでCOPCの表示
- https://viewer.copc.io
- 以下のように直接URLを指定してアクセス  
https://viewer.copc.io/?copc=https://www.example.com/xxx.copc.laz
