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
內文提供繁體中文與巴西葡文完整版本。

Interface em cinco idiomas. Conteúdo completo em chinês tradicional e português do Brasil.

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
