<img width="4099" height="687" alt="mermaid-diagram" src="https://github.com/user-attachments/assets/ef3b4dbc-1863-4970-be18-427dee3dc257" />> 這是課程範本。開始填寫後可以刪除這一行；使用說明見 `docs/getting-started.md`。

# 影像報告撰寫系統設計（課程案例）

雛型網址：https://madeintw886.github.io/report-yzl/

## 1. 使用者研究

### 醫師人物誌

1. 基本資料與角色背景
角色代稱：醫師甲（放射科報告醫師）
【訪談依據】：P.1 使用者角色表、P.2 訪談一標題。
服務機構與工作內容：任職於提供門診與健康檢查服務的醫療機構；主要工作為看醫學影像（PACS）、撰寫並認證影像檢查報告，完成認證後回傳醫院資訊系統（HIS）。
【訪談依據】：P.1 案例背景、使用者角色表、P.2 名詞說明。
負責的檢查報告類型：
門診放射科報告（如胸部 X 光正面、腹部 X 光）
健檢胸部 X 光數位攝影
健檢 2D+3D 乳房攝影
【訪談依據】：P.2 訪談一 第一次訪談「會使用的範本」、P.6 模擬資料（R0001–R0004、R0010）。
系統使用經驗：熟悉本院現行影像報告系統，同時具備其他醫院（A 醫院、B 醫院）系統的使用或觀察經驗，能具體指出 B 醫院打報告畫面的優點，並提供 A、B 醫院的系統截圖作為設計參考。
【訪談依據】：P.3 訪談一 第一次訪談「打報告畫面」及文末括號紀錄。
年資與背景特徵：
【推測】：訪談未提及實際年齡、性別與年資；但從熟悉多家醫院（A、B 醫院）系統介面優缺點，且能明確定義各類門診與健檢報告欄位的精簡需求來看，推測為具備多年臨床閱片經驗的資深放射科醫師。

2. 工作習慣與行為特徵
以工作清單為起點，習慣按檢查時間順序處理個人待辦報告：
【訪談依據】：從工作清單開始工作（P.1 名詞說明）；習慣工作清單預設「登入醫師為報告醫師」，並預設依「檢查日期及時間」排序，且希望每個欄位皆可更改排序（P.2 訪談一 第一次訪談「工作清單需求」）。
重視待辦工作量的即時掌握與視覺狀態區分：
【訪談依據】：希望清單依不同報告項目分類，在明顯位置看到還沒打的「分項數量」及「總數量」（P.3 第二次補充第 2 點），並偏好以不同底色呈現狀態（P.2 第一次訪談「工作清單需求」）。
追求高度流暢、不中斷的連續打報告節奏：
【訪談依據】：希望點選報告即直接呈現 PACS 影像、省去點擊「調閱影像」（P.3 第一次訪談、第二次補充第 5 點）；大量仰賴「片語」快速帶入常用句子（P.2 第一次訪談、P.3 第二次補充）；希望在儲存、認證旁有「上一筆／下一筆」，且在帶入片語確認或儲存後自動跳下一筆報告，不想反覆退回工作清單（P.3 第一次訪談、第二次補充第 7、8 點）。
【推測】：日常門診與健檢待打報告量大、時間壓力高，因此對任何多餘的滑鼠點擊、選單翻找或畫面往返非常敏感。
撰寫報告時需交互參照臨床病歷與歷史影像／報告：
【訪談依據】：打報告時需檢視個案基本資訊（身分證號、姓名、性別、年齡、檢查名稱、開單日期、檢查日期時間、開單醫師）；門診個案需參照 HIS 的「診斷、S、O」（P.3 第一次訪談「打報告畫面」）；同時會查詢病患過去的影像與報告清單，預覽確認後直接帶入（P.3 第一次訪談、第二次補充第 3 點）。
需要中英雙語轉換輔助：
【訪談依據】：撰寫健檢胸 X 與乳攝報告時提到需「配合中翻英」（P.2 第一次訪談），後續補充提到需「具備英翻中功能」（P.3 第二次補充第 6 點）。
【推測】：臨床片語與醫學描述以英文為主（見 P.7 片語範例），但在健檢報告情境或特定欄位中，可能需要將英文專業描述與中文說明互相轉換。
對跨角色分派流程保持防錯警覺：
【訪談依據】：雖然日常由放射師分派指定報告給醫師撰打（P.3 第一次訪談），但擔心放射師未正確分派，因此會主動以日期搜尋查詢當天的報告清單以防漏單（P.3 第二次補充第 4 點）。

3. 使用者目標（Goals）
清楚掌握待打報告數量、不漏單：在工作清單明顯處一眼看到各檢查項目的未完成分項數量與總數，並能隨時在上方調整搜尋條件或查詢當日清單（出處：P.2 第一次訪談「工作清單需求」、P.3 第二次補充第 2、4 點）。
專屬且直覺的操作介面：與放射師 UI 分開互不干擾，並將常用功能直接呈現在畫面空白處，不必進選單翻找（出處：P.3 第一次訪談「打報告畫面」、第二次補充第 1 點）。
單一畫面高速連續完成報告：進入打報告畫面即直接看到影像與精簡後的對應範本欄位，快速帶入片語或歷史報告，儲存／確認後直接跳往下一筆待打報告（出處：P.2–3 第一次訪談、第二次補充第 3、5、7、8 點）。

4. 現行系統痛點與挫折（Frustrations）
與放射師共用介面互相干擾（出處：P.3 第二次補充第 1 點）。
未完成報告的分項數量與總數不夠明顯、位置太下面（出處：P.3 第二次補充第 2 點）。
擔心放射師未正確分派報告醫師而造成漏打（出處：P.3 第二次補充第 4 點）。
看影像需額外點選「調閱影像」，無法在進入打報告畫面時直接呈現（出處：P.3 第一次訪談「打報告畫面」、第二次補充第 5 點）。
許多常用功能藏在選單中，明明畫面有很多空白處卻未直接呈現，操作不便（出處：P.3 第一次訪談「打報告畫面」）。
報告範本包含不需要的欄位（如健檢 2D+3D 乳攝有不需要的 Breast 欄位）（出處：P.2 第一次訪談「會使用的範本」）。
完成一份報告後無法直接跳到下一筆，必須反覆退回工作清單再點選（出處：P.3 第一次訪談「打報告畫面」、第二次補充第 7、8 點）。

### 醫師任務流程

（Mermaid 流程圖，標出痛點發生的步驟）
![Uploading mermai<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 4099.009166666667 687.1999999999999" width="4099.009166666667" height="687.1999999999999" style="--bg:#18181B;--fg:#F4F4F5;--line:#71717A;--muted:#A1A1AA;--surface:#27272A;--border:#3F3F46;background:var(--bg)">
<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&amp;display=swap');
  text { font-family: 'Inter', system-ui, sans-serif; }
  svg {
    /* Derived from --bg and --fg (overridable via --line, --accent, etc.) */
    --_text:          var(--fg);
    --_text-sec:      var(--muted, color-mix(in srgb, var(--fg) 60%, var(--bg)));
    --_text-muted:    var(--muted, color-mix(in srgb, var(--fg) 40%, var(--bg)));
    --_text-faint:    color-mix(in srgb, var(--fg) 25%, var(--bg));
    --_line:          var(--line, color-mix(in srgb, var(--fg) 50%, var(--bg)));
    --_arrow:         var(--accent, color-mix(in srgb, var(--fg) 85%, var(--bg)));
    --_node-fill:     var(--surface, color-mix(in srgb, var(--fg) 3%, var(--bg)));
    --_node-stroke:   var(--border, color-mix(in srgb, var(--fg) 20%, var(--bg)));
    --_group-fill:    var(--bg);
    --_group-hdr:     color-mix(in srgb, var(--fg) 5%, var(--bg));
    --_inner-stroke:  color-mix(in srgb, var(--fg) 12%, var(--bg));
    --_key-badge:     color-mix(in srgb, var(--fg) 10%, var(--bg));
  }
</style>
<defs>
  <marker id="arrowhead" markerWidth="8" markerHeight="5" refX="7" refY="2.5" orient="auto">
    <polygon points="0 0, 8 2.5, 0 5" fill="var(--_arrow)" stroke="var(--_arrow)" stroke-width="0.75" stroke-linejoin="round" />
  </marker>
  <marker id="arrowhead-start" markerWidth="8" markerHeight="5" refX="1" refY="2.5" orient="auto-start-reverse">
    <polygon points="8 0, 0 2.5, 8 5" fill="var(--_arrow)" stroke="var(--_arrow)" stroke-width="0.75" stroke-linejoin="round" />
  </marker>
</defs>
<polyline class="edge" data-from="S1" data-to="S2" data-style="solid" data-arrow-start="false" data-arrow-end="true" points="1175.9122916666674,258.70000000000005 1175.9122916666674,282.70000000000005 654.0226666666674,282.70000000000005 654.0226666666674,306.70000000000005" fill="none" stroke="var(--_line)" stroke-width="1" marker-end="url(#arrowhead)" />
<polyline class="edge" data-from="S2" data-to="S3" data-style="solid" data-arrow-start="false" data-arrow-end="true" points="654.0226666666674,343.6 654.0226666666674,361.6 2133.0080000000007,361.6 2133.0080000000007,379.6" fill="none" stroke="var(--_line)" stroke-width="1" marker-end="url(#arrowhead)" />
<polyline class="edge" data-from="S3" data-to="S4" data-style="solid" data-arrow-start="false" data-arrow-end="true" points="2133.0080000000007,416.5 2133.0080000000007,452.5" fill="none" stroke="var(--_line)" stroke-width="1" marker-end="url(#arrowhead)" />
<polyline class="edge" data-from="S4" data-to="S5" data-style="solid" data-arrow-start="false" data-arrow-end="true" points="2133.0080000000007,489.4 2133.0080000000007,513.4 1163.5401666666671,513.4 1163.5401666666671,513.4" fill="none" stroke="var(--_line)" stroke-width="1" marker-end="url(#arrowhead)" />
<polyline class="edge" data-from="S5" data-to="S6" data-style="solid" data-arrow-start="false" data-arrow-end="true" points="1009.507833333334,513.4 1009.507833333334,513.4 40.04000000000087,513.4 40.04000000000087,100.9 2666.7148500000008,100.9 2666.7148500000008,76.9" fill="none" stroke="var(--_line)" stroke-width="1" marker-end="url(#arrowhead)" />
<polyline class="edge" data-from="S6" data-to="S7" data-style="solid" data-arrow-start="false" data-arrow-end="true" points="2824.4617500000013,76.9 2824.4617500000013,100.9 2524.4541666666673,100.9 2524.4541666666673,124.9" fill="none" stroke="var(--_line)" stroke-width="1" marker-end="url(#arrowhead)" />
<polyline class="edge" data-from="S7" data-to="S8" data-style="solid" data-arrow-start="false" data-arrow-end="true" points="2524.4541666666673,161.8 2524.4541666666673,221.8" fill="none" stroke="var(--_line)" stroke-width="1" marker-end="url(#arrowhead)" />
<polyline class="edge" data-from="S8" data-to="S3" data-style="dotted" data-arrow-start="false" data-arrow-end="true" data-label="現行系統需退回清單重選" points="2483.7470000000008,258.70000000000005 2483.7470000000008,282.70000000000005 2200.8851666666674,282.70000000000005 2200.8851666666674,379.6" fill="none" stroke="var(--_line)" stroke-width="1" stroke-dasharray="4 4" marker-end="url(#arrowhead)" />
<polyline class="edge" data-from="S1" data-to="P1" data-style="solid" data-arrow-start="false" data-arrow-end="false" points="1175.9122916666674,258.70000000000005 1175.9122916666674,282.70000000000005 1162.6446666666675,282.70000000000005 1162.6446666666675,306.70000000000005" fill="none" stroke="var(--_line)" stroke-width="1" />
<polyline class="edge" data-from="S1" data-to="P2" data-style="solid" data-arrow-start="false" data-arrow-end="false" points="1175.9122916666674,258.70000000000005 1175.9122916666674,282.70000000000005 1781.3051666666674,282.70000000000005 1781.3051666666674,306.70000000000005" fill="none" stroke="var(--_line)" stroke-width="1" />
<polyline class="edge" data-from="S2" data-to="P3" data-style="solid" data-arrow-start="false" data-arrow-end="false" points="654.0226666666674,343.6 654.0226666666674,361.6 583.6755000000009,361.6 583.6755000000009,452.5" fill="none" stroke="var(--_line)" stroke-width="1" />
<polyline class="edge" data-from="S5" data-to="P4" data-style="solid" data-arrow-start="false" data-arrow-end="false" points="1086.5240000000003,550.3 1086.5240000000003,574.3 1009.507833333334,574.3 1009.507833333334,598.3" fill="none" stroke="var(--_line)" stroke-width="1" />
<polyline class="edge" data-from="S5" data-to="P5" data-style="solid" data-arrow-start="false" data-arrow-end="false" points="1086.5240000000003,550.3 1086.5240000000003,574.3 3237.8135,574.3 3237.8135,598.3" fill="none" stroke="var(--_line)" stroke-width="1" />
<polyline class="edge" data-from="S6" data-to="P5" data-style="solid" data-arrow-start="false" data-arrow-end="false" points="2824.4617500000013,76.9 2824.4617500000013,100.9 3237.8135,100.9 3237.8135,598.3" fill="none" stroke="var(--_line)" stroke-width="1" />
<polyline class="edge" data-from="S6" data-to="P6" data-style="solid" data-arrow-start="false" data-arrow-end="false" points="2824.4617500000013,76.9 2824.4617500000013,100.9 3738.6701666666672,100.9 3738.6701666666672,513.4" fill="none" stroke="var(--_line)" stroke-width="1" />
<polyline class="edge" data-from="S8" data-to="P7" data-style="solid" data-arrow-start="false" data-arrow-end="false" points="2565.1613333333344,258.70000000000005 2565.1613333333344,282.70000000000005 2848.0231666666673,282.70000000000005 2848.0231666666673,306.70000000000005" fill="none" stroke="var(--_line)" stroke-width="1" />
<g class="edge-label" data-from="S8" data-to="S3" data-label="現行系統需退回清單重選">
  <rect x="2126.3851666666674" y="306.3" width="148.33" height="30.3" rx="2" ry="2" fill="var(--bg)" stroke="var(--_inner-stroke)" stroke-width="1" />
  <text x="2200.5501666666673" y="321.45" text-anchor="middle" font-size="11" font-weight="400" fill="var(--_text-sec)" dy="3.8499999999999996">現行系統需退回清單重選</text>
</g>
<g class="node" data-id="S1" data-label="步驟 1：登入並開啟工作清單（預設登入醫師、依檢查日期時間排序）" data-shape="rectangle">
  <rect x="930.0437916666674" y="221.8" width="491.73699999999997" height="36.900000000000006" rx="0" ry="0" fill="#f0f4f8" stroke="#334e68" stroke-width="1.5px" />
  <text x="1175.9122916666674" y="240.25" text-anchor="middle" font-size="13" font-weight="500" fill="#102a43" dy="4.55">步驟 1：登入並開啟工作清單（預設登入醫師、依檢查日期時間排序）</text>
</g>
<g class="node" data-id="S2" data-label="步驟 2：檢視待打報告數量，調整搜尋條件或查詢當日清單" data-shape="rectangle">
  <rect x="442.9811666666674" y="306.70000000000005" width="422.08299999999997" height="36.900000000000006" rx="0" ry="0" fill="#f0f4f8" stroke="#334e68" stroke-width="1.5px" />
  <text x="654.0226666666674" y="325.15000000000003" text-anchor="middle" font-size="13" font-weight="500" fill="#102a43" dy="4.55">步驟 2：檢視待打報告數量，調整搜尋條件或查詢當日清單</text>
</g>
<g class="node" data-id="S3" data-label="步驟 3：從工作清單點選一筆待打報告，進入打報告畫面" data-shape="rectangle">
  <rect x="1929.3765000000008" y="379.6" width="407.2629999999999" height="36.900000000000006" rx="0" ry="0" fill="#f0f4f8" stroke="#334e68" stroke-width="1.5px" />
  <text x="2133.0080000000007" y="398.05" text-anchor="middle" font-size="13" font-weight="500" fill="#102a43" dy="4.55">步驟 3：從工作清單點選一筆待打報告，進入打報告畫面</text>
</g>
<g class="node" data-id="S4" data-label="步驟 4：檢視個案基本資訊與 HIS 臨床資料（門診診斷、S、O）" data-shape="rectangle">
  <rect x="1907.8875000000007" y="452.5" width="450.241" height="36.900000000000006" rx="0" ry="0" fill="#f0f4f8" stroke="#334e68" stroke-width="1.5px" />
  <text x="2133.0080000000007" y="470.95" text-anchor="middle" font-size="13" font-weight="500" fill="#102a43" dy="4.55">步驟 4：檢視個案基本資訊與 HIS 臨床資料（門診診斷、S、O）</text>
</g>
<g class="node" data-id="S5" data-label="步驟 5：調閱並檢視 PACS 檢查影像，查詢並預覽過去影像與報告" data-shape="rectangle">
  <rect x="855.4755000000005" y="513.4" width="462.097" height="36.900000000000006" rx="0" ry="0" fill="#f0f4f8" stroke="#334e68" stroke-width="1.5px" />
  <text x="1086.5240000000003" y="531.85" text-anchor="middle" font-size="13" font-weight="500" fill="#102a43" dy="4.55">步驟 5：調閱並檢視 PACS 檢查影像，查詢並預覽過去影像與報告</text>
</g>
<g class="node" data-id="S6" data-label="步驟 6：依檢查類別範本撰寫報告（帶入片語、帶入歷史報告、中英翻譯）" data-shape="rectangle">
  <rect x="2561.550250000001" y="40" width="525.8229999999999" height="36.900000000000006" rx="0" ry="0" fill="#f0f4f8" stroke="#334e68" stroke-width="1.5px" />
  <text x="2824.4617500000013" y="58.45" text-anchor="middle" font-size="13" font-weight="500" fill="#102a43" dy="4.55">步驟 6：依檢查類別範本撰寫報告（帶入片語、帶入歷史報告、中英翻譯）</text>
</g>
<g class="node" data-id="S7" data-label="步驟 7：儲存並認證報告（回傳 HIS）" data-shape="rectangle">
  <rect x="2383.4371666666675" y="124.9" width="282.034" height="36.900000000000006" rx="0" ry="0" fill="#f0f4f8" stroke="#334e68" stroke-width="1.5px" />
  <text x="2524.4541666666673" y="143.35000000000002" text-anchor="middle" font-size="13" font-weight="500" fill="#102a43" dy="4.55">步驟 7：儲存並認證報告（回傳 HIS）</text>
</g>
<g class="node" data-id="S8" data-label="步驟 8：切換至下一筆待打報告" data-shape="rectangle">
  <rect x="2402.3326666666676" y="221.8" width="244.243" height="36.900000000000006" rx="0" ry="0" fill="#f0f4f8" stroke="#334e68" stroke-width="1.5px" />
  <text x="2524.454166666668" y="240.25" text-anchor="middle" font-size="13" font-weight="500" fill="#102a43" dy="4.55">步驟 8：切換至下一筆待打報告</text>
</g>
<g class="node" data-id="P1" data-label="痛點 A（步驟 1）：醫師與放射師 UI 未分開，互相干擾（訪談一第二次補充 1）" data-shape="rectangle">
  <rect x="893.0641666666675" y="306.70000000000005" width="539.1610000000001" height="36.900000000000006" rx="0" ry="0" fill="#ffe3e3" stroke="#c92a2a" stroke-width="1.5px" />
  <text x="1162.6446666666675" y="325.15000000000003" text-anchor="middle" font-size="13" font-weight="500" fill="#7f1d1d" dy="4.55">痛點 A（步驟 1）：醫師與放射師 UI 未分開，互相干擾（訪談一第二次補充 1）</text>
</g>
<g class="node" data-id="P2" data-label="痛點 B（步驟 1-2）：未打報告的分項數量與總數不明顯、位置太下面（訪談一第二次補充 2）" data-shape="rectangle">
  <rect x="1460.2251666666675" y="306.70000000000005" width="642.16" height="36.900000000000006" rx="0" ry="0" fill="#ffe3e3" stroke="#c92a2a" stroke-width="1.5px" />
  <text x="1781.3051666666674" y="325.15000000000003" text-anchor="middle" font-size="13" font-weight="500" fill="#7f1d1d" dy="4.55">痛點 B（步驟 1-2）：未打報告的分項數量與總數不明顯、位置太下面（訪談一第二次補充 2）</text>
</g>
<g class="node" data-id="P3" data-label="痛點 C（步驟 2）：搜尋條件未直接列在上方，調整篩選條件麻煩；且擔心放射師未正確分派需額外查當日清單（訪談一第一次訪談、第二次補充 4、訪談三）" data-shape="rectangle">
  <rect x="51.04000000000087" y="452.5" width="1065.271" height="36.900000000000006" rx="0" ry="0" fill="#ffe3e3" stroke="#c92a2a" stroke-width="1.5px" />
  <text x="583.6755000000009" y="470.95" text-anchor="middle" font-size="13" font-weight="500" fill="#7f1d1d" dy="4.55">痛點 C（步驟 2）：搜尋條件未直接列在上方，調整篩選條件麻煩；且擔心放射師未正確分派需額外查當日清單（訪談一第一次訪談、第二次補充 4、訪談三）</text>
</g>
<g class="node" data-id="P4" data-label="痛點 D（步驟 3-5）：進入打報告畫面時影像未直接呈現，須手動點選「調閱影像」（訪談一第一次訪談、第二次補充 5）" data-shape="rectangle">
  <rect x="597.2848333333341" y="598.3" width="824.4459999999999" height="36.900000000000006" rx="0" ry="0" fill="#ffe3e3" stroke="#c92a2a" stroke-width="1.5px" />
  <text x="1009.507833333334" y="616.75" text-anchor="middle" font-size="13" font-weight="500" fill="#7f1d1d" dy="4.55">痛點 D（步驟 3-5）：進入打報告畫面時影像未直接呈現，須手動點選「調閱影像」（訪談一第一次訪談、第二次補充 5）</text>
</g>
<g class="node" data-id="P5" data-label="痛點 E（步驟 5-6）：許多功能藏在選單中不方便，畫面空白處未被善用；且缺乏過去影像含報告直接查詢與帶入（訪談一第一次訪談、第二次補充 3）" data-shape="rectangle">
  <rect x="2729.2605000000003" y="598.3" width="1017.1060000000001" height="36.900000000000006" rx="0" ry="0" fill="#ffe3e3" stroke="#c92a2a" stroke-width="1.5px" />
  <text x="3237.8135" y="616.75" text-anchor="middle" font-size="13" font-weight="500" fill="#7f1d1d" dy="4.55">痛點 E（步驟 5-6）：許多功能藏在選單中不方便，畫面空白處未被善用；且缺乏過去影像含報告直接查詢與帶入（訪談一第一次訪談、第二次補充 3）</text>
</g>
<g class="node" data-id="P6" data-label="痛點 F（步驟 6）：現行範本有多餘欄位（如健檢乳攝的 Breast 欄位）（訪談一第一次訪談）" data-shape="rectangle">
  <rect x="3418.3311666666673" y="513.4" width="640.6779999999999" height="36.900000000000006" rx="0" ry="0" fill="#ffe3e3" stroke="#c92a2a" stroke-width="1.5px" />
  <text x="3738.6701666666672" y="531.85" text-anchor="middle" font-size="13" font-weight="500" fill="#7f1d1d" dy="4.55">痛點 F（步驟 6）：現行範本有多餘欄位（如健檢乳攝的 Breast 欄位）（訪談一第一次訪談）</text>
</g>
<g class="node" data-id="P7" data-label="痛點 G（步驟 7-8）：無「上一筆／下一筆」按鈕，也無法在儲存或確認片語後自動跳下一筆，必須退回工作清單重新點選（訪談一第一次訪談、第二次補充 7、8）" data-shape="rectangle">
  <rect x="2298.7151666666673" y="306.70000000000005" width="1098.616" height="36.900000000000006" rx="0" ry="0" fill="#ffe3e3" stroke="#c92a2a" stroke-width="1.5px" />
  <text x="2848.0231666666673" y="325.15000000000003" text-anchor="middle" font-size="13" font-weight="500" fill="#7f1d1d" dy="4.55">痛點 G（步驟 7-8）：無「上一筆／下一筆」按鈕，也無法在儲存或確認片語後自動跳下一筆，必須退回工作清單重新點選（訪談一第一次訪談、第二次補充 7、8）</text>
</g>
</svg>d-diagram.svg…]()


### 痛點

| 痛點 | 出處 | 對醫師的影響 |
| --- | --- | --- |
| | | |

## 2. 需求矛盾與設計決定

| 議題 | 不一致的說法 | 我的設計決定 | 理由 |
| --- | --- | --- | --- |
| | | | |

## 3. 設計範圍

- 本設計涵蓋：
- 不涵蓋及原因：

## 4. 設計變數與回應

- 收到的變數：
- 影響分析：
- 回應方式（全面調整／部分調整／協商）與理由：

## 5. 設計演進

### 第一版

### 替代方案與選擇理由

### 啟發式評估與設計變數後的修改

### 可用性測試後的修改
