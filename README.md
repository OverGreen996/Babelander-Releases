# Babelander 譯鄉人

**全方位 PC 遊戲即時翻譯助手**

字幕、裝備、任務、聊天與回覆，一套完成。

[下載最新版](https://github.com/OverGreen996/Babelander-Releases/releases/latest) · [v1.4.3 安裝版](https://github.com/OverGreen996/Babelander-Releases/releases/download/v1.4.3/Babelander-1.4.3-Setup.exe)

此儲存庫僅包含官方發布說明與授權資料，不包含 Babelander 應用程式原始碼。GitHub 自動產生的 Source code 壓縮檔只有本庫文件；一般使用者請下載 Setup 或 Windows-Lite。

目前版本：**1.4.3**。本版統一品牌、專有授權、安裝授權頁、關於頁及公開更新來源。

前版新增整張卡片成本摘要、每日／本期功能用量分析、DeepL 官方用量手動同步、安全估算與明確的服務時區。Metrics 預設只記字數、雜湊及安全欄位，全文除錯需主動開啟且只暫存記憶體。詳見 [雲端額度診斷](CLOUD_DIAGNOSTICS.md)。

前版已修正 Google／Azure／DeepL 設定流程：填好 Key 後按「完成」會先儲存並顯示各家使用確認，不必先測試連線才能出現在引擎清單。取消確認保留視窗；外層設定頁「完成」也會補問漏掉的同意。此流程不自動送出測試文字、不切換引擎、不解除額度鎖。

Babelander 是一套為 PC 遊戲玩家設計的即時翻譯助手，整合遊戲字幕、裝備資訊、任務內容、遊戲聊天與中文→英文回覆，並支援本機與多種雲端翻譯服務。

## 1.4.3 各功能引擎與按需暖機

字幕、裝備、任務、中文→英文回覆可各自選本機、Google、Azure 或 DeepL。預設全部本機；**聊天室來訊永遠只在本機處理**。儲存 Key／測試成功不會自動選用雲端。卡片先用既有詞典與規則，只把尚未解決的文字交給所選服務；驗證仍共用原本核心。

一般啟動只做環境檢查，模型維持 COLD。真正使用本機翻譯才共用一次暖機；停止所有使用模型的功能後，預設閒置 5 分鐘釋放，可改 1／10 分鐘或不釋放。選用 Full Local Mode 則啟動時暖機。下載仍需自行點擊，未下載模型也可使用已設定的雲端功能。

「聊天翻譯 → 中文→英文回覆」可獨立開啟，無須先框選或啟動監測。收合保留草稿，停止監測／切換遊戲／隱藏聊天面板不會取消回覆；Enter 翻譯後仍由你自行回遊戲貼上。

各雲端服務有獨立排程器，正常翻譯最多同時 2 筆，本機最多 1 筆。過期字幕取消尚未送出的工作；已送出結果不再顯示，已嘗試用量仍保留。

遇到額度限制會暫停受影響功能並詢問暫用本機、其他已設定服務或維持暫停，**不改永久設定**。在設定可恢復永久設定；重開程式清除暫用，但已知服務額度限制仍保存。成功測試確認恢復才解除未知的服務限制；不由發票日期推算 Azure 重置日。DeepL Developer 總額度不按月重置，Growth 依實際月繳／年繳週期，舊 API Free 另行辨別。

各服務以 SQLite 分開計算 attempted／confirmed 字元。本機安全上限為 Google 每美西月份 450,000 字、Azure 每美西月份 1,900,000 字；DeepL 依自訂每期字數與 1–31 日重置（短月取月底，Developer／年繳不月重置）。送出前原子預扣，超限即停止；這是應用限制，不是官方免費額度。雲端設定提供事件更新的用量資源條，未設定服務不背景連線。逾時可能已送達，因此安全上限採 attempted。舊版本用量只遷移成 attempted，不捏造 confirmed。

設定與下載 → 雲端翻譯服務設定提供獨立 Key、同意、測試與完整教學：

- [Google 教學](docs/google_api_setup_zh-TW.html)
- [Azure 教學](docs/azure_api_setup_zh-TW.html)
- [DeepL 教學](docs/deepl_api_setup_zh-TW.html)

Key 仍以 Windows DPAPI 加密，服務只接受列出的官方 HTTPS 端點。從舊版擴大使用到字幕／卡片時會重新確認文字傳送範圍。教學用系統瀏覽器開啟，不包含 WebEngine／Chromium；REST 不依賴大型 Provider SDK。

## 安裝、更新與解除安裝

- 一般使用者下載 **Babelander-1.4.3-Setup.exe**，依畫面完成安裝，不需要 Python。
- 公開發布不提供 Babelander 應用程式原始碼。LGPL 第三方原始碼另列於同版 Release，見 THIRD_PARTY_SOURCE.md。
- **Babelander-1.4.3-Windows-Lite.zip** 保留給免安裝使用者與舊版更新入口。
- 不附翻譯模型與下載式執行元件；首次使用請在「設定與下載」自行下載。
- 安裝版程式在 `%LOCALAPPDATA%/Programs/Babelander`，模型、設定、自訂辭典與快取在 `%LOCALAPPDATA%/Babelander`。
- **升級不用解除安裝**：按「檢查更新」→ 下載新版 → 關閉 Babelander → 執行新版 Setup。原有模型與設定會保留。
- **解除安裝會刪除模型、執行元件、設定、自訂辭典與快取**。可從 Windows 已安裝的應用程式或開始功能表解除安裝；需要保留的資料請先備份。
- 原有免安裝版不會自動搬移。關閉舊版後，可將其 `data`、`models`、`runtime` 複製到上述安裝版資料目錄；保留 `.babelander-owner` 識別檔。驗證成功後再自行清理舊版。

## 啟動自檢與按需暖機

每次開啟檢查模型檔案大小與標頭、執行元件、OCR 檔案及辭典。一般模式完成自檢後維持 COLD，不啟動 OCR 或模型。Full Local Mode 才在啟動時暖機模型；擷取仍需自行開始。缺少檔案請手動下載，完成後重新自檢。

啟動檢查不連網，也不會每次讀完整個模型做雜湊。下載時仍做完整 SHA-256 校驗；驅動或其他系統相依問題會在暖機時顯示錯誤，可修正後按「載入／暖機模型」重試。使用上次儲存的效能模式；暖機後模型會占用記憶體或顯存，關閉程式或手動卸載模型可釋放。

## 回覆小窗

聊天分頁或浮層控制鈕可獨立開啟中翻英回覆，小窗可拖曳並記住位置，收合保留本次草稿。隱藏或停止聊天監測不影響回覆。草稿不保存到硬碟，程式不會自動切回遊戲或發送。

## GitHub 更新來源

https://github.com/OverGreen996/Babelander-Releases/releases

只在點擊時檢查公開正式 Release，不傳送畫面或聊天資料。私有儲存庫或尚無正式 Release 可能回傳 404。發布標籤使用 `v1.4.3`，安裝檔使用 `Babelander-版本-Setup.exe`，免安裝版使用 `Babelander-版本-Windows-Lite.zip`。安裝版會選取 Setup，免安裝版選取 ZIP；下載後由使用者執行，不會在背景自行安裝。

## 首次啟動

1. 將精簡分享版完整解壓到可寫入的資料夾，例如 Documents/Babelander。不要在 ZIP 內直接執行或只複製 EXE。
2. 執行 Babelander.exe，前往「設定與下載」。
3. 點「下載模型與執行元件」，等待下載與 SHA-256 校驗完成。
4. 載入本地模型，切換需要的功能並框選遊戲文字。

首次下載約 1.93 GB，請預留至少 5 GB 磁碟空間。下載來源為 Hugging Face 與 llama.cpp GitHub Releases；下載會在使用者點擊後開始，支援中斷續傳。完成後翻譯可離線使用。啟動、文字辨識所需的 Python／Qt 環境、小型 OCR 模型及繁簡轉換資料已包含在精簡版中。

## 功能

- 英文 → 繁體中文即時字幕與裝備／任務翻譯。
- 裝備 Rare 樣式花邊依名稱顏色調整，外框貼齊框選範圍；文字自動縮放，內容過多時可捲動。
- 聊天增量追蹤、長句換行與緊湊顯示；暫時隱藏時繼續監測。
- 中文 → 英文回覆；Enter 翻譯、Shift+Enter 換行。英文僅複製到剪貼簿，不自動貼上或發送到遊戲。
- 浮層旁控制鈕切換互動／滑鼠穿透；聊天花邊背景可開關，預設關閉。
- 自訂辭典、分領域參考詞條、本機模型效能設定。
- 深色 MMO 介面與透明古金色劍環 Logo。

## 使用與資料

平台為 Windows x64，建議先用視窗或無邊框模式測試。OCR／翻譯依畫面清晰度、字型與電腦效能而異；可能出現誤譯。複雜中文回覆仍需核對英文。

安裝版設定與自訂資料存於 `%LOCALAPPDATA%/Babelander/data`；免安裝版存於程式旁的 data 資料夾。聊天及聊天回覆只保留在記憶體。分享程式前不要附上自己的 data、models、runtime 或 downloads。更新前關閉舊版，避免相同快捷鍵衝突。

本機回歸與封裝測試不代表已完成所有真實遊戲、多螢幕 DPI 或 Microsoft 注音候選視窗的驗收。

## 授權與官方版本

Copyright © 2026 OverGreen996. All Rights Reserved.

Babelander 官方版本免費提供個人使用，採 Proprietary 授權，並非開放原始碼。
未經作者 OverGreen996 書面授權，不得修改後重新發布、重新散布、重新打包、轉售、出租、再授權、改名發行、移除作者或授權資訊，或冒充官方版本。

若透過非官方管道付費取得本軟體，請向販售者申請退費，並從官方頁面重新下載。
歡迎分享 [官方發布庫](https://github.com/OverGreen996/Babelander-Releases) 及 [官方 Release](https://github.com/OverGreen996/Babelander-Releases/releases)。

完整條款請參閱 [LICENSE](LICENSE)。第三方 Open Source 元件仍依其各自原始授權條款提供，本程式的授權不限制第三方授權權利；詳見 [第三方聲明](THIRD_PARTY_NOTICES.md)、[第三方原始碼與替換說明](THIRD_PARTY_SOURCE.md) 及 licenses/。
字典與素材來源見 reference/README.md 及 ASSET_PROVENANCE.md。SHA256SUMS.txt 可核對發布附件。
