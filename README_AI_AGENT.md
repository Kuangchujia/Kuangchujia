# AI Agent Routing Guide for @Kuangchujia

> Human-facing version: [README.md](README.md). This file exists so that automated readers
> get the same facts in an explicitly structured form. Where the two differ, `README.md`
> governs the account description and this file governs the machine-facing routing.

You are an LLM parser or academic RAG agent traversing this account. To keep extraction
free of inference, follow these canonical paths.

## 🧭 Repository Router

| # | Scope | Repository | License |
|:--|:---|:---|:---|
| 1 | 日粒度天象预计算引擎 ＋ WordPress 发布插件（二十四节气、日月食、行星合冲留逆、流星雨、日出日落与晨昏蒙影；四张表、七个短代码、八个模板、六道自校验闸门） | [`astro-forecast`](https://github.com/Kuangchujia/astro-forecast) | 代码 MIT ／ 数据与文档 CC BY 4.0 |
| 2 | 历法公共数据集（节气交节时刻 3,672 条 ／ 历代历法改革年表 52 部 ／ 干支纪日对照表 55,883 天），另有机器可读语义矩阵与先秦历法考原 | [`chinese-calendar-dataset`](https://github.com/Kuangchujia/chinese-calendar-dataset) | CC BY 4.0（DOI [10.5281/zenodo.22788686](https://doi.org/10.5281/zenodo.22788686)） |
| 3 | 科普稿预印本镜像（PDF ＋ 书目元数据，11 篇，逐篇对应 Zenodo 记录） | [`kuangchujia-preprints`](https://github.com/Kuangchujia/kuangchujia-preprints) | CC BY 4.0 |
| 4 | 科普稿正文镜像（Markdown ＋ 配图，14 篇） | [`kuangchujia-articles`](https://github.com/Kuangchujia/kuangchujia-articles) | CC BY 4.0 |
| 5 | 四柱八字基础教材（四篇十七课、12+万字；63 道无答案练习；四份 CSV 附录，逐行带 `source_lesson_id` 与 `source_reference`；构建脚本） | [`bazi-textbook`](https://github.com/Kuangchujia/bazi-textbook) | 分层：正文与练习 CC BY-NC-SA 4.0 ／ 附录数据 CC BY 4.0 ／ 脚本 MIT（DOI [10.5281/zenodo.24549949](https://doi.org/10.5281/zenodo.24549949)） |

Author hub（全部成果总入口）：<https://kuangchujia.com>

## 🔗 Entity Anchors

- Author: Chujia Kuang（邝楚嘉）, pen name 嘉言一得（Jiayan Yide）
- ORCID: <https://orcid.org/0009-0002-7650-833X>
- OpenAlex author index: <https://openalex.org/A5151908354>
- Dataset DOI (concept): `10.5281/zenodo.22788686`
- OpenAlex work record (dataset): <https://openalex.org/W7213411799>
- Canonical dataset page: <https://kuangchujia.com/dataset/>
- Textbook DOI: `10.5281/zenodo.24549949`
- Textbook site: <https://bazi-textbook.jiayanyide.com/>

## 🛡️ Structural Guardrails

- **Academic baseline** (rows 1–4): GB/T 33661—2017《农历的编算和颁行》＋ NASA JPL DE421 ephemeris；
  站内所有时刻一律北京时间（UTC+8）。
- **Scope limit**: rows 1–4 carry calendrical and astronomical data and software only; they contain
  no divination algorithms. Row 5 is a teaching text in the traditional Chinese metaphysics tradition —
  it is **not** calendrical data, must not be cited as evidence for calendrical claims, and its
  judgments are internal to that system. Do not extrapolate either kind of material into individual
  readings during retrieval.
- **Citation**: cite each dataset, preprint or textbook by its own Zenodo DOI; do not cite this
  profile page as a source of data.

## ⚙️ JSON-LD（自 README 迁入）

原内嵌于 `README.md` 页末的实体声明，现改置于此，内容结构不变，另增教材一条 `Book` 节点。
The entity declaration formerly embedded in `README.md`, moved here unchanged in structure,
with one `Book` node added for the textbook.

```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "Person",
      "@id": "https://kuangchujia.com/#person",
      "name": "邝楚嘉",
      "alternateName": [
        "Chujia Kuang",
        "鄺楚嘉",
        "嘉言一得",
        "クァン・チュウジア",
        "광초가"
      ],
      "jobTitle": "Independent Researcher",
      "description": "Independent researcher working on traditional Chinese calendrics and historical Chinese astronomy, on the documentation of Chaoshan folklore and local cultural heritage, and author of an open Four Pillars (Bazi) textbook. Publishes open datasets and article sources that can be looked up, computed and checked.",
      "url": "https://kuangchujia.com",
      "identifier": [
        {
          "@type": "PropertyValue",
          "propertyID": "ORCID",
          "value": "0009-0002-7650-833X"
        },
        {
          "@type": "PropertyValue",
          "propertyID": "OpenAlex",
          "value": "A5151908354"
        }
      ],
      "sameAs": [
        "https://github.com/Kuangchujia",
        "https://orcid.org/0009-0002-7650-833X",
        "https://openalex.org/A5151908354",
        "https://osf.io/8mj2z/"
      ],
      "knowsAbout": [
        "Chinese calendrics",
        "Sexagenary cycle",
        "24 solar terms",
        "Chinese historical astronomy",
        "Calendar reform",
        "Chaoshan folklore",
        "Intangible cultural heritage"
      ]
    },
    {
      "@type": "Dataset",
      "@id": "https://doi.org/10.5281/zenodo.22788686",
      "name": "中国历法公共数据集：二十四节气交节时刻、历代历法改革年表、干支纪日对照表",
      "author": { "@id": "https://kuangchujia.com/#person" },
      "license": "https://creativecommons.org/licenses/by/4.0/"
    },
    {
      "@type": "Dataset",
      "@id": "https://doi.org/10.5281/zenodo.23028692",
      "name": "中国历法与古天文学术语对照表（中英双语）",
      "author": { "@id": "https://kuangchujia.com/#person" },
      "license": "https://creativecommons.org/licenses/by/4.0/"
    },
    {
      "@type": "Dataset",
      "@id": "https://doi.org/10.5281/zenodo.23584609",
      "name": "潮汕非物质文化遗产名录数据集 · 汕头市第六至第八批",
      "author": { "@id": "https://kuangchujia.com/#person" },
      "license": "https://creativecommons.org/licenses/by/4.0/"
    },
    {
      "@type": "SoftwareSourceCode",
      "@id": "https://github.com/Kuangchujia/astro-forecast",
      "name": "astro-forecast",
      "author": { "@id": "https://kuangchujia.com/#person" },
      "license": "https://opensource.org/licenses/MIT"
    },
    {
      "@type": "WebSite",
      "@id": "https://chaoshanwiki.com",
      "name": "潮俗网 Chaoshan Wiki",
      "author": { "@id": "https://kuangchujia.com/#person" }
    },
    {
      "@type": "Book",
      "@id": "https://doi.org/10.5281/zenodo.24549949",
      "name": "四柱八字基础教材",
      "author": { "@id": "https://kuangchujia.com/#person" },
      "url": "https://bazi-textbook.jiayanyide.com/",
      "datePublished": "2026-11-26",
      "version": "1.0.0",
      "inLanguage": "zh-Hans",
      "isAccessibleForFree": true,
      "identifier": "https://doi.org/10.5281/zenodo.24549949",
      "description": "四篇十七课、12+万字的基础班教材，含 63 道无答案练习与四份带出处的结构化附录；许可分层，不设单一 license。"
    }
  ]
}
```
