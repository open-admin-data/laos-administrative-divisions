# Laos Administrative Divisions / ສາທາລະນະລັດ ປະຊາທິປະໄຕ ປະຊາຊົນລາວ

Open dataset of Laos' administrative hierarchy — from provinces (ແຂວງ) through districts (ເມືອງ) down to villages (ບ້ານ). This repository provides structured, bilingual (Lao + English) reference data for all three levels of Lao administrative divisions, including geographic coordinates at every level. Designed for developers, researchers, government agencies, and AI agents.

Licensed under CC-BY-4.0. Browse the hierarchy through GitHub's folder navigation, download aggregate files in JSON/CSV/NDJSON, or integrate directly via raw URLs.

## Overview

| Item | Details |
|------|---------|
| Province | 18 |
| District | 148 |
| Village | 13,330 |
| Coordinates | ✅ Included (all levels) |
| Formats | JSON, NDJSON, CSV |
| License | CC-BY-4.0 |
| Last Updated | 2026-05-16 |

## Browse by Province

| # | Province | Districts | Villages | Link |
|---|----|----|----|------|
| 1 | ແຂວງອັດຕະປື (Attapeu) | 4 | 213 | [Browse](divisions/attapeu-at/) |
| 2 | ແຂວງບໍ່ແກ້ວ (Bokeo) | 5 | 345 | [Browse](divisions/bokeo-bk/) |
| 3 | ແຂວງບໍລິຄຳໄຊ (Bolikhamsai) | 7 | 487 | [Browse](divisions/bolikhamsai-bl/) |
| 4 | ແຂວງຈຳປາສັກ (Champasak) | 11 | 1,068 | [Browse](divisions/champasak-ch/) |
| 5 | ແຂວງຫົວພັນ (Houaphan) | 9 | 1,003 | [Browse](divisions/houaphan-ho/) |
| 6 | ແຂວງຄຳມ່ວນ (Khammouane) | 9 | 778 | [Browse](divisions/khammouane-kh/) |
| 7 | ແຂວງຫຼວງນ້ຳທາ (Luang Namtha) | 5 | 465 | [Browse](divisions/luang-namtha-lm/) |
| 8 | ແຂວງຫລວງພະບາງ (Luang Prabang) | 11 | 1,373 | [Browse](divisions/luang-prabang-lp/) |
| 9 | ແຂວງອຸດົມໄຊ (Oudomxay) | 7 | 889 | [Browse](divisions/oudomxay-ou/) |
| 10 | ແຂວງຜົ້ງສາລີ (Phongsaly) | 7 | 794 | [Browse](divisions/phongsaly-ph/) |
| 11 | ແຂວງສາລະວັນ (Salavan) | 8 | 776 | [Browse](divisions/salavan-sl/) |
| 12 | ແຂວງສະຫວັນນະເຂດ (Savannakhet) | 16 | 1,634 | [Browse](divisions/savannakhet-sv/) |
| 13 | ແຂວງວຽງຈັນ (Vientiane Province) | 11 | 597 | [Browse](divisions/vientiane-province-vi/) |
| 14 | ນະຄອນຫຼວງວຽງຈັນ (Vientiane Capital) | 9 | 334 | [Browse](divisions/vientiane-capital-vt/) |
| 15 | ແຂວງໄຊຍະບູລີ (Xaignabouli) | 11 | 610 | [Browse](divisions/xaignabouli-xa/) |
| 16 | ແຂວງເຊກອງ (Xekong) | 4 | 386 | [Browse](divisions/xekong-xe/) |
| 17 | ແຂວງຊຽງຂວາງ (Xiangkhouang) | 9 | 1,384 | [Browse](divisions/xiangkhouang-xi/) |
| 18 | ເຂດພິເສດໄຊສົມບູນ (Xaisomboun) | 5 | 194 | [Browse](divisions/xaisomboun-xn/) |

## Data Files

| File | Format | Description |
|------|--------|-------------|
| [all-province.json](data/all-province.json) | JSON | All 18 province records |
| [all-district.json](data/all-district.json) | JSON | All 148 district records |
| [village-by-province/](data/village-by-province/) | JSON | 13,330 villages split by province |
| [all-flat.json](data/all-flat.json) | JSON | Levels 1-2 flat array |
| [all-flat.ndjson](data/all-flat.ndjson) | NDJSON | Streaming format |
| [all-flat.csv](data/all-flat.csv) | CSV | Spreadsheet format |
| [hierarchy.json](data/hierarchy.json) | JSON | Nested tree |
| [schema.json](data/schema.json) | JSON Schema | Data schema |

## Quick Start

### Python

```python
import json

with open("data/all-province.json", "r", encoding="utf-8") as f:
    data = json.load(f)

for r in data:
    print(f"{r['name']['local']} ({r['name']['en']}) — {r['children_count']['district']} districts")
```

### JavaScript

```javascript
import { readFileSync } from "fs";

const data = JSON.parse(readFileSync("data/all-province.json", "utf-8"));
console.log(`Total: ${data.length} provinces`);
```

## Schema

| Field | Type | Description |
|-------|------|-------------|
| `id` | string | Unique identifier |
| `level` | integer | 1=province, 2=district, 3=village |
| `level_name` | object | Level label (local + English) |
| `name.local` | string | Name in local script |
| `name.en` | string | English name |
| `name.slug` | string | URL-safe slug |
| `parent` | object/null | Parent division reference |
| `ancestors` | array | Full ancestor chain |
| `children_count` | object | Count of children per level |
| `zip_codes` | array | Postal codes (where available) |
| `geo.lat` | string | Latitude (WGS84) |
| `geo.lon` | string | Longitude (WGS84) |

Full schema: [data/schema.json](data/schema.json)

## Hierarchy Browse

```
divisions/{province-slug}/
divisions/{province-slug}/{district-slug}/
```

Villages are listed inline in each district's README.

## AI Integration

- [llms.txt](docs/llms.txt) — Quick reference for AI agents
- [llms-full.txt](docs/llms-full.txt) — Summary with per-province links
- [Per-province data](docs/llms-full/) — Full data by province

## Citation

```
Laos Administrative Divisions Dataset (CC-BY-4.0)
URL: https://github.com/open-admin-data/laos-administrative-divisions
```

See [CITATION.cff](CITATION.cff) for machine-readable citation.

## License

- **Data**: [CC-BY-4.0](LICENSE)

## Related

- [ListBase](https://www.listbase.org) — Structured reference data for every country
- [open-admin-data](https://github.com/open-admin-data) — Open administrative data for ASEAN countries
- [thailand-administrative-divisions](https://github.com/open-admin-data/thailand-administrative-divisions) — Thailand dataset
