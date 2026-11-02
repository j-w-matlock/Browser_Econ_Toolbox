# Econ Toolbox

A single-file, offline web app for U.S. Army Corps of Engineers (USACE) water resources economics: expected annual damage, cost annualization, HEC-FDA 2.0 and HEC-FIA post-processing, recreation and water supply analyses, and report-ready charts, tables, and narratives.

> [!WARNING]
> **Not a certified model.** Double check all math and logic, and verify every result before using it in an official report.
>
> This is not an official USACE product and is not endorsed by the U.S. Army Corps of Engineers.

## Quick start

1. Download [Econ-Toolbox.html](Econ-Toolbox.html): open the file on GitHub and click **Download raw file**, or use **Code > Download ZIP**.
2. Double-click the file to open it in Chrome, Edge, Firefox, or Safari.
3. Pick a module in the left sidebar. Many modules open with sample values; replace them with your study's data.

The **User Manual** at the top of the sidebar has step-by-step instructions for every module, data import formats, formulas, and a glossary.

There is nothing to install: no server, plugins, extensions, or admin rights, and no internet connection once the file is open.

## Modules

### Core economics

| Module | What it does |
| --- | --- |
| Expected Annual Damage | Integrates the AEP-damage curve (trapezoidal rule, ER 1105-2-100) for multiple damage categories, with optional stage and equivalent annual damage (EqAD). |
| Cost Annualizer | Annualizes first costs with the capital recovery factor: multiple scenarios, interest during construction (IDC), future costs, benefits breakdown, cost updates, sunk cost ratio (SCRB), BCR, and the unity-BCR first cost. |
| Traffic Delay Analysis | Expected annual traffic delay cost (EATDC) of flood detours: vehicle operating cost plus value of time, integrated over flood frequency and duration. |
| Advanced Bridge Replacement | Annual equivalent benefit of replacing a bridge now vs. extending the existing structure. |

### HEC-FDA 2.0 analysis

| Module | What it does |
| --- | --- |
| Structure Inventory Analysis | Descriptive statistics, distribution tests, Cochran sample sizes, and composition breakdowns for structure inventory `.dbf` files (for example, NSI exports). |
| Stage Damage Organizer | Multi-alternative stage-damage editor that imports HEC-FDA 2.0 StructureStageDamageDetails CSVs or `.sqlite` stage-damage relationships, with EAD and damage category, occupancy type, and asset breakdowns. |
| HEC-FDA Economics Helper | Post-processes HEC-FDA 2.0 results (`.sqlite` or CSV): EAD summary, damage disaggregation, performance and assurance metrics, EqAD, NED benefits and BCR comparison, and a structure inventory report built from an FDA study folder. |
| FDA Export Helpers | Browses and visually edits HEC-FDA 2.0 study input functions (frequency, stage-discharge, transforms, levee fragility, occupancy types) and re-exports them as FDA ASCII import text or a new `.sqlite`. The original file is never modified. |

### Recreation

| Module | What it does |
| --- | --- |
| Unit Day Value | Six recreation valuation methods: Unit Day Value, Travel Cost, Hedonic Pricing, Contingent Valuation, Choice Modeling, and Benefit Transfer. |
| Recreation Capacity | Seasonal capacity (persons at one time, daily capacity, user-days) for camping, fishing, and boating. |

### Water management

| Module | What it does |
| --- | --- |
| Updated Cost of Storage | Escalates original joint-use costs with ENR/CWCCIS indices, allocates them by storage share, adds RR&R, and annualizes two scenarios. |
| Water Demand Forecast | Projects municipal, industrial, and agricultural water demand from population and per-capita trends, sector shares, and system adjustments for a baseline and two alternatives. |
| FIA/WCM Analysis | Generates ER 1110-2-8156 Section 4-12 socioeconomic narratives for Water Control Manual updates from HEC-FIA results, Headwaters Economics EPS workbooks, and USDA Cropland Data Layer rasters, and exports the section as a Word report. |

### Diagramming

| Module | What it does |
| --- | --- |
| Diagram Builder | Excalidraw-style whiteboard for flow charts, conceptual models, and report figures: shapes, arrows, text, images, symbols, and emoji. Opens and saves `.excalidraw` files. |
| Brackets | Double-elimination or round-robin tournament brackets with seeding and scores. |

## Saving your work

The toolbox does not auto-save, and closing or refreshing the tab erases unsaved work. An **Unsaved changes** badge appears in the toolbar after edits, and the browser asks before you leave the page.

- **Save Project** (Ctrl+S) downloads a `.json` file with every module's inputs. **Load Project** restores it. Project files are human-readable JSON.
- **Save to Browser** keeps a copy in this browser's local storage and restores it the next time the page opens. If browser storage runs short, datasets read from files are left out, so use Save Project to keep everything.

## Importing data

| Data | File types | Modules |
| --- | --- | --- |
| Tables (AEP-damage, AEP-duration, stage-damage, and similar) | `.csv`, `.txt`, `.json` through the toolbar **Import Data** button | Most calculation modules, such as EAD, Traffic Delay, Cost Annualizer, and Stage Damage Organizer |
| HEC-FDA 2.0 results tables | `.csv` through each tab's **Import CSV** button | HEC-FDA Economics Helper |
| HEC-FDA 2.0 study or results database | `.sqlite` | HEC-FDA Economics Helper, Stage Damage Organizer, FDA Export Helpers |
| HEC-FDA 2.0 structure stage-damage details | StructureStageDamageDetails `.csv` | Stage Damage Organizer, HEC-FDA Economics Helper |
| Structure inventory attributes | Shapefile `.dbf` | Structure Inventory Analysis, HEC-FDA Economics Helper |
| HEC-FIA results | `runs` folder (`EconResults.dbf`) or Results Summary `.xlsx` | FIA/WCM Analysis |
| Headwaters Economics EPS profiles | Demographics and Key Indicators `.xlsx` | FIA/WCM Analysis |
| USDA Cropland Data Layer | Watershed-clipped GeoTIFF (`.tif`) | FIA/WCM Analysis |
| Drawings and shape libraries | `.excalidraw`, `.excalidrawlib` | Diagram Builder |
| Team lists | `.txt`, `.csv` | Brackets |

See **User Manual > Data Import** for column names and step-by-step instructions.

## Exporting results

- **Export Charts & Tables** (top of each module): every chart and table on the page as one Word document (editable native charts and Word tables), one Excel workbook (native charts with their data), or PNG images.
- **Copy Chart** (above each chart): an editable Excel or Word chart file, or a picture on the clipboard. **Copy Table** (above results tables): paste the table into Word or Excel.
- **Export Report** (toolbar): an HTML report of all modules with results, tables, and charts, ready to print or save as PDF.
- **FIA/WCM Analysis > Export Report**: a Word document laid out as a finished Section 4-12, with numbered captions and editable charts.
- **FDA Export Helpers**: FDA 2.0 ASCII import text, or a new `.sqlite` holding the selected elements.
- **Diagram Builder** and **Brackets**: PNG or SVG files, or a PNG on the clipboard. Diagram Builder also saves `.excalidraw` scenes.

## Requirements

- A current version of Chrome, Edge, Firefox, or Safari on Windows, macOS, or Linux.
- Excel (`.xlsx`) imports use the browser's built-in decompression: Chrome or Edge 103+, Firefox 113+, or Safari 16.4+.

## Privacy

Everything runs locally in your browser. Files you open are read in place and never uploaded, and the app makes no network requests.

## Guidance references

Methods follow the USACE guidance cited in the User Manual, including ER 1105-2-100 (Planning Guidance Notebook), ER 1105-2-101 and EM 1110-2-1619 (flood risk analysis), ER 1110-2-8156 (water control manuals), and ER 1110-2-1302 (Civil Works cost engineering). Discount rates, price levels, and analysis periods are inputs: set them for your study.

## Repository contents

| File | Description |
| --- | --- |
| `Econ-Toolbox.html` | The complete app: HTML, CSS, JavaScript, and bundled libraries in one file. |
| `index.html` | Identical copy of `Econ-Toolbox.html`. |
| `README.md` | This file. |

## Development

There is no build step and nothing to install. Edit `Econ-Toolbox.html` in a code editor such as VS Code and reload it in the browser. If you keep `index.html`, copy the edited file over it so the two stay identical.

## Acknowledgements

- [sql.js](https://github.com/sql-js/sql.js) (MIT License) is bundled to read and write HEC-FDA `.sqlite` files.
- The Diagram Builder adapts the drawing approaches of [Rough.js](https://github.com/rough-stuff/rough) and [perfect-freehand](https://github.com/steveruizok/perfect-freehand) and uses the [Excalidraw](https://github.com/excalidraw/excalidraw) file format (all MIT License).
- Emoji and symbol names come from [unicode-emoji-json](https://github.com/muan/unicode-emoji-json) (MIT License), [Unicode CLDR](https://github.com/unicode-org/cldr-json), and the Unicode Character Database.
