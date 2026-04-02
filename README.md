# 4ager

A command-line field tool for mushroom foragers. Identify species by traits, check what's fruiting in your region, and get full edibility and safety profiles before you eat anything.

## Usage

```bash
python3 mushroom_forager.py <command> [options]
```

### `identify` — match a mushroom by its traits

```bash
python3 mushroom_forager.py identify --cap-color yellow --habitat oak --spore-print white
python3 mushroom_forager.py identify --cap-color orange --gill-type "true gills" --habitat "dead wood"
python3 mushroom_forager.py identify --cap-color white --spore-print white --habitat grassland
```

Available trait flags:

| Flag | Example values |
|---|---|
| `--cap-color` | yellow, red, brown, white, orange |
| `--cap-shape` | convex, flat, funnel-shaped, shelf, honeycomb |
| `--gill-type` | true gills, false gills, pores, ridges, spines |
| `--gill-color` | white, pink, orange, cream |
| `--stem-color` | white, ring, hollow, net-like |
| `--spore-print` | white, brown, black, pale yellow, lilac |
| `--habitat` | oak, dead wood, grassland, pine, meadow |
| `--smell` | fruity, earthy, unpleasant, anise |
| `--flesh-color` | white, yellow, blues when cut |

Results are ranked by match percentage. Deadly species are flagged prominently regardless of rank.

---

### `calendar` — what's fruiting in your region this month

```bash
python3 mushroom_forager.py calendar --region pacific-northwest --month 10
python3 mushroom_forager.py calendar --region europe --month 5
```

Supported regions: `north-america`, `europe`, `pacific-northwest`, `northeast-us`, `southeast-us`, `midwest-us`, `uk`, `central-europe`

---

### `safety` — full profile for a named species

```bash
python3 mushroom_forager.py safety chanterelle
python3 mushroom_forager.py safety "death cap"
python3 mushroom_forager.py safety porcini
```

Returns traits, season, regions, look-alikes, and safety warnings.

---

### `list` — all species in the database

```bash
python3 mushroom_forager.py list
```

## Species database

19 species across edibility categories:

| Edibility | Species |
|---|---|
| Choice edible | Chanterelle, King Bolete / Porcini, Morel, Lion's Mane, Oyster Mushroom, Hen of the Woods |
| Edible | Chicken of the Woods, Giant Puffball, Field Mushroom, Shaggy Mane, Honey Fungus |
| Toxic | Fly Agaric, Jack-o'-lantern, False Morel, Yellow Stainer, Satan's Bolete, Common Earthball |
| Deadly | Death Cap, Destroying Angel |

## Safety

This tool is for reference only. Never eat a wild mushroom based solely on this tool. Always:

- Cross-check with multiple field guides
- Consult an experienced local forager
- Slice puffballs fully to check interior
- Do the yellow-stain test on white Agaricus species
- When in doubt, throw it out

## Adding species

Species are defined in `data/mushrooms.json`. Each entry includes traits, season (months 1–12), regions, edibility, look-alikes, and warnings. Add new entries following the existing schema.
