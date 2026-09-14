# BYD Brasil Radar

比亞迪巴西市場雷達 · Painel de inteligência de mercado da BYD no Brasil

單頁儀表板，追蹤比亞迪在巴西的市場位置：以巴西汽車市場為大環境，上牌量前十名品牌為主要競爭，近三年進軍巴西的中國品牌為次要競品。

Painel de página única que acompanha a posição da BYD no Brasil: o mercado automotivo brasileiro como pano de fundo, as dez marcas com mais emplacamentos como concorrência principal e as marcas chinesas que entraram no país nos últimos três anos como concorrência secundária.

## 分頁 / Abas

| 分頁 | Aba | 內容 |
|---|---|---|
| 市場新聞 | Notícias | 主題 × 巴西地區熱力圖、篩選、18 則情報卡片 |
| BYD 戰情 | Estratégia BYD | 戰略機會、銷售量能、車型戰情、卡馬薩里工廠 |
| 巴西車市 | Mercado Brasil | 市場總量、電動化技術別構成 |
| 主要競品 Top 10 | Top 10 rivais | 上牌量前十名品牌，點選比較市佔 |
| 中國品牌 | Marcas chinesas | 已有本地產能 / 已正式營運 / 已確認進入 |
| 法規與關稅 | Regras & tarifas | Gecex-Camex 關稅階梯、法規條目 |

## 語言 / Idiomas

介面支援五語系：繁中、简中、EN、PT-BR、日本語。

| 語系 | 內文 | 作法 |
|---|---|---|
| 繁中 | 完整 | 原始撰寫語言，所有 base 欄位 |
| 简中 | 完整 | 執行期自動轉換（見下） |
| PT-BR | 完整 | 人工撰寫，`欄位_pt` |
| EN | 部分 | 僅標題與摘要有 `欄位_en`，其餘回退繁中 |
| 日本語 | 僅介面 | 內文回退繁中 |

### 繁→簡轉換機制

內文以繁中撰寫，簡中不另存一份副本，而是在渲染時轉換，分兩道：

1. **用詞對應** `SC_PHRASES` — 台灣／大陸用語差異：資料→数据、通路→渠道、級距→细分市场、頭期→首付、法人→企业、品質→质量、行銷→营销、訊號→信号、車款→车型、量能→销量、網路→网络、試算→测算
2. **字元對應** `SC_MAP` — 290 字的繁簡對照表，由本檔實際使用的字集產生，非手工輸入；另加 `SC_EXTRA` 三字（後→后、於→于、拚→拼），因為產生器對一對多的字會保守跳過

記錄上若有明確的 `欄位_zh-Hans` 會優先採用。日文介面用到的日文漢字（売 実 戦 読 覧 値 録 頼 関）刻意不轉換。

新增內文時只要寫繁中 base 欄位，簡中會自動跟上；但若用到目前字集以外的字，需要重新產生 `SC_MAP`。

Interface em cinco idiomas. Conteúdo completo em chinês tradicional, chinês simplificado (convertido em tempo de execução) e português do Brasil. Em inglês há apenas títulos e resumos; em japonês, somente a interface.

## 資料來源 / Fontes

所有數字均附來源連結。主要來源：

- [Fenabrave](https://www.fenabrave.org.br/portalv2/Conteudo/Emplacamentos) — 上牌量
- [ABVE](https://abve.org.br/) — 電動化滲透率
- [Gecex / MDIC](https://www.gov.br/mdic/pt-br/assuntos/camex/estrategia-comercial/resolucoes-gecex-sobre-alteracoes-tarifarias) — 進口關稅

### 資料品質注意事項

- 品牌排行數字彙整自轉述 Fenabrave 的媒體來源，**未逐項比對官方報表**，站上標示為 `data quality: medium`。
- Fenabrave 的「automóveis」口徑只含乘用車，品牌排行榜含輕型商用車，兩者不可直接相減。站上以黃色提示框標出。
- 標示為「本站計算」或「目標」的數字非官方實績。
- 各中國品牌的首次上市年份多數未能查證，故未列出。

本站為市場情報彙整，非投資建議。

## 開發 / Desenvolvimento

單一 `index.html`，無建置步驟。資料與渲染邏輯都在檔案內的 `<script>` 區塊：

- `META` / `NEWS` — 摘要與情報卡片
- `BYDDATA` — BYD 戰情
- `MARKET` — 巴西車市
- `BRANDS` — 前十大品牌
- `CHINA` — 中國品牌
- `REGDATA` — 法規與關稅

新增語系：在 `UI` 加入該語系的鍵值，並在資料物件加上 `欄位_語系` 覆寫（例如 `headline_pt`）。未提供覆寫時自動回退到繁體中文。

外部相依：Chart.js（cdnjs）、Google Fonts。
