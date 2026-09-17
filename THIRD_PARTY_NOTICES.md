# Babelander 譯鄉人 — Third-party notices

Babelander 自有內容依根目錄 Babelander Software License 提供。下列第三方著作權仍屬其原作者，並非 OverGreen996 的 All Rights Reserved 內容。各第三方授權的使用、修改與散布權利不受本程式專有授權縮減。

## Qt / PySide / Shiboken

實際建置版本：Qt 6.11.2、PySide6 Essentials 6.11.2、Shiboken6 6.11.2。
Copyright The Qt Company Ltd. and other contributors. 本程式使用 LGPLv3 授權選項。完整 LGPLv3 與 GPLv3 文本位於 `licenses/Qt/`，原始版權、Qt 內含第三方授權及其他授權選項保留於 `licenses/Qt/upstream/` 及 `licenses/PySide6_Essentials/upstream/`。

QtCore、QtGui、QtWidgets、QtNetwork、QtSvg 及圖像／平台外掛以 DLL 動態載入，未靜態連結進 Babelander。未修改上游函式庫原始碼。
使用者可依適用 LGPL 條款修改、替換及重新連結相容函式庫，並為除錯此類修改進行逆向工程。Babelander 自有應用程式程式碼依 Babelander Software License 授權。
第三方原始碼在同版官方 Release 提供，含 PySide 與 Shiboken；網址、雜湊、編譯入口與替換說明見 [THIRD_PARTY_SOURCE.md](THIRD_PARTY_SOURCE.md)。

## GEOS

Shapely 2.1.2 的幾何運算 DLL 包含 GEOS 3.13.1（LGPLv2.1；Copyright GEOS contributors）。動態 DLL 位於 `_internal/Shapely.libs/`，可依 LGPL 使用、修改、替換相容版本及散布 GEOS。授權、版權見 `licenses/GEOS/` 與 `licenses/shapely/`；同版 Release 另附 GEOS 完整原始碼與編譯說明。

## Python、OCR 與其他執行元件

Python 3.12.14 使用 PSF 與所含第三方授權，見 `licenses/Python/`。RapidOCR 3.9.2 及其內附 PP-OCRv6 小型 OCR 模型依上游 Apache-2.0 與模型聲明提供；來源 https://github.com/RapidAI/RapidOCR 及 https://github.com/PaddlePaddle/PaddleOCR 。ONNX Runtime 採 MIT；OpenCC 採 Apache-2.0；OpenCV 依其 wrapper MIT、OpenCV Apache-2.0 及內含元件授權；NumPy 依 BSD 與所含元件授權；mss 採 MIT；tzdata 2026.4 依 Apache-2.0 與 IANA 資料聲明。完整原始授權與 NOTICE 保留於對應 licenses 目錄。

PyInstaller 6.22.2 bootloader 使用 GPL 與 distribution exception；該例外允許封裝專有應用程式，不把 Babelander 自有內容改為 GPL。原文位於 `licenses/pyinstaller/`。
Windows／Microsoft Visual C++ DLL 依其原始 Microsoft runtime 散布條款提供，並非 Babelander 自有內容；Python/Qt 套件中的原始聲明予以保留。
未使用的 FFmpeg 影片外掛及 Mesa OpenGL 軟體驅動不隨本版封裝；本程式使用 Qt Widgets／QPainter 平面介面及靜態圖像 OCR。

## 明確點擊才下載的模型與 Runtime（不包含在 Setup / Lite）

Qwen3-1.7B（bartowski Q4_K_M 轉換）依上游 Apache-2.0：https://huggingface.co/Qwen/Qwen3-1.7B 。llama.cpp b10896 依 MIT：https://github.com/ggml-org/llama.cpp 。隨 llama.cpp 提供的 CUDA 12.4 archive 依 NVIDIA CUDA redistribution terms：https://docs.nvidia.com/cuda/eula/index.html 。使用者在程式中主動點擊下載後，從上游取得模型與 runtime；本版不將其塞入安裝包。

## Dependency inventory

此清單涵蓋 requirements-lock.txt 的開發／建置環境，不表示所有測試或建置工具都會執行於使用者電腦。實際封裝輸入由 PyInstaller Analysis 核對歸屬；版本與授權文字雜湊記錄於 dependency_licenses.json，發布時附 BUNDLED_DEPENDENCIES.json 列出實際封裝的 Python 套件。

| Distribution | Version | License summary | Retained texts |
|---|---|---|---|
| `Markdown` | 3.10.2 | BSD-3-Clause | `licenses/Markdown/` |
| `PySide6_Essentials` | 6.11.2 | LGPL-3.0-only OR GPL-2.0-only OR GPL-3.0-only | `licenses/PySide6_Essentials/` |
| `PyYAML` | 6.0.3 | MIT | `licenses/PyYAML/` |
| `Pygments` | 2.21.0 | BSD-2-Clause | `licenses/Pygments/` |
| `altgraph` | 0.17.5 | MIT | `licenses/altgraph/` |
| `antlr4-python3-runtime` | 4.9.3 | BSD | `licenses/antlr4-python3-runtime/` |
| `certifi` | 2026.7.22 | MPL-2.0 | `licenses/certifi/` |
| `charset-normalizer` | 3.5.1 | MIT | `licenses/charset-normalizer/` |
| `colorama` | 0.4.6 | See retained upstream license | `licenses/colorama/` |
| `colorlog` | 6.12.0 | MIT License | `licenses/colorlog/` |
| `flatbuffers` | 25.12.19 | Apache 2.0 | `licenses/flatbuffers/` |
| `idna` | 3.19 | BSD-3-Clause | `licenses/idna/` |
| `iniconfig` | 2.3.0 | MIT | `licenses/iniconfig/` |
| `mss` | 10.2.0 | See retained upstream license | `licenses/mss/` |
| `numpy` | 2.5.3 | BSD-3-Clause AND 0BSD AND MIT AND Zlib AND CC0-1.0 | `licenses/numpy/` |
| `omegaconf` | 2.3.1 | See retained upstream license | `licenses/omegaconf/` |
| `onnxruntime` | 1.30.0 | MIT License | `licenses/onnxruntime/` |
| `opencc-python-reimplemented` | 0.1.7 | Apache License | `licenses/opencc-python-reimplemented/` |
| `opencv-python` | 5.0.0.93 | Apache 2.0 | `licenses/opencv-python/` |
| `packaging` | 26.3 | Apache-2.0 OR BSD-2-Clause | `licenses/packaging/` |
| `pefile` | 2024.8.26 | MIT | `licenses/pefile/` |
| `pillow` | 12.3.0 | MIT-CMU | `licenses/pillow/` |
| `pip` | 25.0.1 | MIT | `licenses/pip/` |
| `pluggy` | 1.6.0 | MIT | `licenses/pluggy/` |
| `protobuf` | 7.36.1 | 3-Clause BSD License | `licenses/protobuf/` |
| `psutil` | 7.2.2 | BSD-3-Clause | `licenses/psutil/` |
| `pyclipper` | 1.4.0 | MIT | `licenses/pyclipper/` |
| `pyinstaller-hooks-contrib` | 2026.7 | See retained upstream license | `licenses/pyinstaller-hooks-contrib/` |
| `pyinstaller` | 6.22.2 | See retained upstream license | `licenses/pyinstaller/` |
| `pytest` | 9.1.1 | MIT | `licenses/pytest/` |
| `pywin32-ctypes` | 0.2.3 | BSD-3-Clause | `licenses/pywin32-ctypes/` |
| `rapidocr` | 3.9.2 | Apache-2.0 | `licenses/rapidocr/` |
| `requests` | 2.34.2 | Apache-2.0 | `licenses/requests/` |
| `setuptools` | 84.0.0 | MIT | `licenses/setuptools/` |
| `shapely` | 2.1.2 | BSD 3-Clause | `licenses/shapely/` |
| `shiboken6` | 6.11.2 | LGPL-3.0-only OR GPL-2.0-only OR GPL-3.0-only | `licenses/shiboken6/` |
| `six` | 1.17.0 | MIT | `licenses/six/` |
| `tqdm` | 4.70.0 | MPL-2.0 AND MIT | `licenses/tqdm/` |
| `urllib3` | 2.7.0 | MIT | `licenses/urllib3/` |
| `tzdata` | 2026.4 | Apache-2.0 | `licenses/tzdata/` |

## 字典與素材

字典為專案自行建立的參考內容，依所有者提供的來源確認記錄於 reference/README.md；不宣稱一般短詞專屬所有權。素材來源與 AI 輔助處理記錄於 ASSET_PROVENANCE.md。
