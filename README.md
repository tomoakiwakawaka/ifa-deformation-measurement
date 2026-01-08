# ifa-deformation-measurement

## Overview（概要）

点群データ(PCD/PLY)を用いて、IFAの圧力印加時の収縮量($L, w$)および体積変化を計測するコード

This repository contains code to measure shrinkage amounts ($L, w$) and volume changes of IFA (Inflatable Actuator) during pressure application using point cloud data (PCD/PLY format).

## Requirements（必要なライブラリ）

このプロジェクトでは以下のライブラリを使用します：

### Python バージョン
- Python >= 3.8

### 必須ライブラリ
- **Open3D** >= 0.17.0 - 点群データの読み込み、可視化、処理
- **NumPy** >= 1.21.0 - 数値計算
- **SciPy** >= 1.7.0 - 科学技術計算

### オプショナルライブラリ
- **matplotlib** >= 3.4.0 - データ可視化
- **pandas** >= 1.3.0 - データ分析

### PCL (Point Cloud Library) について
Open3Dを使用するため、PCLのインストールは必須ではありません。より高度な点群処理が必要な場合は、python-pclまたはpcl-pythonを別途インストールしてください。

### インストール方法

```bash
pip install -r requirements.txt
```

## Data Structure（データ構成）

計測データ（点群ファイル）は以下のフォルダ構成で管理することを推奨します：

```
ifa-deformation-measurement/
├── README.md
├── requirements.txt
├── src/                          # ソースコード
│   ├── measure_deformation.py    # 変形計測メインスクリプト
│   ├── volume_calculation.py     # 体積計算モジュール
│   └── utils.py                  # ユーティリティ関数
├── data/                         # 計測データディレクトリ
│   ├── raw/                      # 生の点群データ
│   │   ├── before_pressure/      # 圧力印加前のデータ
│   │   │   ├── sample01.pcd
│   │   │   ├── sample01.ply
│   │   │   └── ...
│   │   └── after_pressure/       # 圧力印加後のデータ
│   │       ├── sample01_10kPa.pcd
│   │       ├── sample01_20kPa.pcd
│   │       └── ...
│   ├── processed/                # 処理済みデータ
│   │   └── aligned/              # 位置合わせ済みデータ
│   └── results/                  # 計測結果
│       ├── deformation_L.csv     # 長さ方向の収縮量
│       ├── deformation_w.csv     # 幅方向の収縮量
│       └── volume_change.csv     # 体積変化
├── notebooks/                    # Jupyter notebooks（解析・可視化用）
│   └── analysis.ipynb
├── tests/                        # テストコード
│   └── test_measurement.py
└── docs/                         # ドキュメント
    └── measurement_procedure.md  # 計測手順書
```

### データファイル形式

- **PCD形式**: Point Cloud Data（PCLおよびOpen3D対応）
- **PLY形式**: Polygon File Format（汎用的な3Dデータ形式）

### データ命名規則の例

```
<サンプルID>_<条件>.pcd
例：
- sample01.pcd          # 圧力印加前
- sample01_10kPa.pcd    # 10kPa印加時
- sample01_20kPa.pcd    # 20kPa印加時
```

## Usage（使用方法）

```python
import open3d as o3d
import numpy as np

# 点群データの読み込み
pcd_before = o3d.io.read_point_cloud("data/raw/before_pressure/sample01.pcd")
pcd_after = o3d.io.read_point_cloud("data/raw/after_pressure/sample01_10kPa.pcd")

# 変形量の計測
# （実装予定）
```

## License

MIT License
