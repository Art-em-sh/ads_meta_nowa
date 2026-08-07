# NOWA — wave1 ads

Сопоставление текстов и креативов для первой волны объявлений Meta (7 «дверей» × варианты A/B).

- **Источник текстов:** `NOWA_тексты_объявления.docx`
- **Источник картинок:** `NOWA_wave1_creatives/` (Downloads)
- **Единый файл сопоставления:** [`ads_mapping.json`](./ads_mapping.json) — источник правды. Все поля объявления (заголовок, основной текст, кнопка, ссылка с UTM, картинка) собраны туда per-вариант.

## Структура

```
NOWA_wave1_ads/
├── ads_mapping.json     ← сопоставление текст + картинка для каждого из 14 объявлений
├── README.md
└── creatives/
    ├── 01_son-1_A.png
    ├── 02_son-1_B.png
    ├── 03_son-2_A.png
    ├── 04_son-2_B.png
    ├── 05_telo-1_A.png
    ├── 06_telo-1_B.png
    ├── 07_telo-4_A.png
    ├── 08_telo-4_B.png
    ├── 09_calm-4_A.png
    ├── 10_calm-4_B.png
    ├── 11_calm-2_A.png
    ├── 12_calm-2_B.png
    ├── 13_head-1_A.png
    └── 14_head-1_B.png
```

Имя файла = `<порядковый номер>_<дверь>_<вариант>.png`, однозначно привязано к полю `variants[].image_file` в JSON — перепутать местами невозможно.

## Двери

| door_id | Заголовок | Лендинг |
|---|---|---|
| son-1 | Как засыпать быстрее | now-a.life/lp/son-1 |
| son-2 | Как высыпаться за те же часы | now-a.life/lp/son-2 |
| telo-1 | Как разгрузить шею и плечи | now-a.life/lp/telo-1 |
| telo-4 | Как распрямить спину | now-a.life/lp/telo-4 |
| calm-4 | Как перестать накручиваться | now-a.life/lp/calm-4 |
| calm-2 | Как перестать срываться | now-a.life/lp/calm-2 |
| head-1 | Как вернуть ясность | now-a.life/lp/head-1 |

## UTM-схема

- `utm_source={{site_source_name}}` — динамическая подстановка платформы показа (Meta: fb/ig/an/msg)
- `utm_medium=initiate_checkout` — кампания оптимизирована под событие InitiateCheckout
- `utm_content=<door_id>_<A|B>` — идентификатор конкретного креатива, из исходного документа

## Meta launch

Кампания создаётся отдельным шагом через Meta Ads MCP на основе `ads_mapping.json` (поля `image_github_raw_url`, `primary_text_resolved`, `headline`, `cta_button`, `destination_url`). Статус запуска фиксируется отдельно, в этом файле — только сопоставление контента.
