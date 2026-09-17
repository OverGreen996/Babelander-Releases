# Third-party source access and library replacement — 1.4.5

本文件提供 LGPL 第三方函式庫原始碼，不授權或公開 Babelander 自有應用程式原始碼。
官方發布庫由 OverGreen996 控制：https://github.com/OverGreen996/Babelander-Releases

## 同版原始碼下載

上述發布庫的 **v1.4.5** Release 同時提供下列未修改上游 source archives，可免費取得，無需下載 Babelander 原始碼、付費或索取許可。這些附件必須與二進位檔同時可用，不得僅以外部上游 URL 代替。

| Source archive | SHA-256 |
|---|---|
| [qtbase-everywhere-src-6.11.2.tar.xz](https://github.com/OverGreen996/Babelander-Releases/releases/download/v1.4.5/qtbase-everywhere-src-6.11.2.tar.xz) | `5b2e00eccaf5a4d8c14134ffa0ea8dfd0a35ae1ffc7f8d87fa4305a1ed23cf22` |
| [qtsvg-everywhere-src-6.11.2.tar.xz](https://github.com/OverGreen996/Babelander-Releases/releases/download/v1.4.5/qtsvg-everywhere-src-6.11.2.tar.xz) | `d594337feca84c26fb67fe87b85e6a5c12fda404b611d905f9d138210c311876` |
| [qtimageformats-everywhere-src-6.11.2.tar.xz](https://github.com/OverGreen996/Babelander-Releases/releases/download/v1.4.5/qtimageformats-everywhere-src-6.11.2.tar.xz) | `cecd8900f34b6550076309bc94f62f828008b633a4239e0a08c86788f41001f8` |
| [pyside-setup-everywhere-src-6.11.2.tar.xz](https://github.com/OverGreen996/Babelander-Releases/releases/download/v1.4.5/pyside-setup-everywhere-src-6.11.2.tar.xz) | `cba47efbaad1bedd529725cbc14e21f156c7a19366f07b3edfbb076ffd7afdf8` |
| [geos-3.13.1.tar.bz2](https://github.com/OverGreen996/Babelander-Releases/releases/download/v1.4.5/geos-3.13.1.tar.bz2) | `df2c50503295f325e7c8d7b783aca8ba4773919cde984193850cf9e361dfd28c` |

qtbase 包含 QtCore／Gui／Widgets／Network 及平台、TLS、基本圖像外掛；qtsvg 包含 SVG 模組及外掛；qtimageformats 包含額外圖像外掛。Qt 模組均為 6.11.2。pyside-setup 6.11.2 包含 PySide6、Shiboken6、typesystems、生成器、CMake 與上游建置腳本。GEOS 3.13.1 包含 Shapely 所載入幾何 DLL 的來源。各 archive 含完整原始碼、原始授權與上游編譯指令；本專案未修改上述第三方來源。

原始下載 URL、位元組大小與 SHA-256 記錄在 third_party_sources.json，供獨立核對。授權文本另包含於 licenses/；Qt/PySide LGPLv3 與 GPLv3、GEOS LGPLv2.1 權利保留。

## 在 Windows 替換相容函式庫

1. 關閉 Babelander。先備份完整免安裝資料夾；建議在另一份 Windows-Lite 測試副本操作，避免影響使用中的模型及設定。
2. 使用 source archive 中 README、CMakeLists.txt、configure／setup.py 指令，編譯 Windows x64 Release、相同 ABI 的函式庫。Qt 使用共享庫（-shared），使用 MSVC 與相容 Windows SDK；保持 Core/Gui/Widgets/Network/Svg、platforms/qwindows 和需用的圖像外掛版本一致。Qt configure 及 CMake 參數見 qtbase/README.md 與上游：https://doc.qt.io/qt-6/windows-building.html 。PySide/Shiboken 建置說明見 pyside-setup/README.md、sources/shiboken6/doc/README.md 與 https://doc.qt.io/qtforpython-6/building_from_source/index.html 。GEOS 使用 CMake，BUILD_SHARED_LIBS=ON，見 archive/README.md。
3. Qt DLL、PySide 的 QtCore/QtGui/QtWidgets .pyd 與 pyside6.abi3.dll 在 `_internal/PySide6/`；Qt 外掛在其 `plugins/`。Shiboken binding 位於 `_internal/shiboken6/`；GEOS DLL 在 `_internal/Shapely.libs/`。GEOS 的上游 wheel 使用帶雜湊的 DLL 檔名；使用相容編譯並維持 loader/import table 所需檔名，或依 Shapely 上游建置方式重建匹配的 binding。
4. 以相容版本替換測試副本中的相應檔案；不要只混換互不相容的單一 Qt DLL。應用程式沒有針對這些函式庫的簽章／雜湊鎖或啟動時還原機制。啟動 Babelander.exe，或在測試副本執行 `Babelander.exe --self-test` 驗證 GUI、OCR 與相依功能。
5. 自動更新不會背景覆寫；使用者自行執行新版 Setup 時會以新版套件替換程式檔，修改過的函式庫應自行保留。

LGPL 允許的函式庫修改、替換、重新連結及為除錯該等修改的逆向工程不受 Babelander 專有授權縮減。函式庫的合法散布依其原始授權辦理。本說明不要求公開 Babelander 自有程式碼，也不將 Babelander 的品牌及自有內容重新授權為 LGPL。

若附件無法取得，請在官方發布庫開 Issue 聯繫 OverGreen996。發行者應保留對應版本附件及雜湊；公開发布程序會核對附件完整上傳後才發布二進位檔。
