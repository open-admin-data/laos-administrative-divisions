# Methodology

## Data Sources

This dataset is compiled from multiple open sources:

- **geoBoundaries** (CC BY 4.0) — ADM1 (province) and ADM2 (district) polygon boundaries with ISO 3166-2 codes for centroid computation and hierarchy
- **GeoNames** (CC BY 4.0) — Populated place records with coordinates, used for village-level data (13,330 records)

## Processing

1. Province boundaries from geoBoundaries ADM1 → centroid computation + ISO code extraction
2. District boundaries from geoBoundaries ADM2 → centroid computation + spatial join to provinces
3. Village points from GeoNames (feature class P = populated places) → spatial join to districts via point-in-polygon
4. Multi-format export: JSON, NDJSON, CSV
5. Hierarchy folder structure with READMEs generated via EJS templates

## Structure

- **18 provinces** (17 provinces + Vientiane Capital prefecture)
- **148 districts** (ເມືອງ muang)
- **13,330 villages** from GeoNames populated places (broader than the census ~8,400 due to inclusion of hamlets and localities)

## Romanization

English names use BGN/PCGN romanization conventions as found in geoBoundaries and GeoNames. Note that Lao romanization varies across sources (e.g., Houaphan/Houaphanh/Huaphan, Xaignabouli/Sainyabuli).

## Accuracy

- Province and district coordinates computed from official geoBoundaries polygons
- Village coordinates from GeoNames (WGS84 points)
- 100% coordinate coverage at all levels
- Parent assignment: provinces via ISO code, districts via point-in-polygon, villages via point-in-polygon with nearest-neighbour fallback
- Build script is idempotent: same input always produces same output