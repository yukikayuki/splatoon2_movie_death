# splatoon2_movie_death

スプラトゥーン2のプレイ動画から、やられたシーンを切り出すJupyterのノートブックです。
初めから学習済みモデルが入っているので、すぐにやられたシーン切り出しをお試し頂けます。

[Qiita記事](https://qiita.com/tfandkusu/items/acbc0906046bb7b2b1db)

# setup docker-compose.yml
volumesの`<動画のあるディレクトリ>:/home/jovyan/src_movie`を環境に合わせて変更する。


# docker
```bash
docker-compose up -d
open http://localhost:8888
```

# command
```bash
# 準備
# docker-compse upした初回にライブラリをインストール
docker-compose exec notebook pip install opencv-python tensorflow tqdm
# Jupyterノートブックをpythonに変換
docker-compose exec notebook jupyter nbconvert cut_movie.ipynb --to python

# 実行
# 最新の録画ファイルに対して処理を実行
docker-compose exec notebook python cut_movie.py
# ファイルを指定しての実行例
docker-compose exec notebook python cut_movie.py src_movie/2021-02-23_17-48-28.mp4
```
