# Large-Scale Assessment Data

## 概要
PISAやTIMSSといった大規模学力調査のcsvファイルです。そのうち増やしていく予定・・・。


## library.tar.gzについて
[Colab](https://colab.research.google.com/)でRを動かすときに，[intsvy](https://cran.r-project.org/web/packages/intsvy/index.html)のダウンロードに時間がかかるので，
事前にlibraryを圧縮・解凍することで時短を図っています。`.ipynb`に以下のように入力するとPISAの分析が可能です。

```R
# ダウンロード
system("curl -L -o library.tar.gz https://github.com/kawa5902/LSAdata/raw/refs/heads/main/202412library.tar.gz")
# 解凍
system("tar -xzf /content/library.tar.gz -C /content")
.libPaths("library")

# library
library(intsvy)

# データのダウンロード
url <- "https://github.com/kawa5902/LSAdata/raw/refs/heads/main/pisa2012stuJPN.csv"
jpn2012 <- read.csv(url)

# 数学リテラシーの平均値
pisa.mean.pv(paste0("PV", 1:5, "MATH"), data = jpn2012)
# PV1の平均値
pisa.mean("PV1MATH", data = jpn2012)
# 男女（ST04Q01）別の数学リテラシーの平均値
pisa.mean.pv(paste0("PV", 1:5, "MATH"), by = "ST04Q01", data = jpn2012)
```


## 参考
[How to quickly re-install R packages in Google Colab](https://www.tanyongsheng.com/note/how-to-quickly-re-install-r-packages-in-google-colab/): 参考にしたサイト。Rのtarだとreshapeがうまく圧縮できなかったので，systemを使って圧縮・解凍しています。
