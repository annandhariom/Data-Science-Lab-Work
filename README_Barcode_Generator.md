# 🏷️ Barcode Generator

## Description

This project generates **real, scannable barcodes** for products in a mini retail inventory catalog using Python. Given product information such as Product ID, Name, Price, Category, and Stock, the program:

- Builds a structured product catalog using Pandas
- Performs exploratory data analysis and inventory visualization
- Generates **Code128** barcodes (for alphanumeric product IDs)
- Generates **EAN-13** barcodes (standard 13-digit retail format)
- Creates styled **product labels** combining barcode images with product metadata
- Produces a full **batch report** of all generated barcode files

This is a practical mini-application that mirrors real-world inventory and retail management systems.

---

## Dataset

- **Source:** User-defined / Custom (no external dataset required)
- **Description:** A manually created product catalog of 12 items across 6 categories:
  - **Electronics** — Headphones, Speaker, Keyboard, Mouse, USB Hub
  - **Books** — Python Programming Book, Data Science Handbook
  - **Kitchen** — Coffee Mug
  - **Stationery** — Notebook Set
  - **Fitness** — Yoga Mat, Water Bottle
  - **Home Office** — Desk Lamp LED

| Field       | Description                        |
|-------------|------------------------------------|
| ProductID   | Unique string ID (e.g., PRD001)    |
| Name        | Product display name               |
| Price       | Price in USD                       |
| Category    | Product category                   |
| Stock       | Units available in inventory       |
| TotalValue  | Price × Stock (computed column)    |

---

## Steps Performed

1. **Data Setup**
   - Defined a 12-product catalog as a Python list of dictionaries
   - Loaded into a Pandas DataFrame
   - Computed `TotalValue = Price × Stock`

2. **Exploratory Data Analysis**
   - Computed overall stats: price range, average price, total stock, total inventory value
   - Grouped by Category for aggregated summary (item count, avg price, total value)

3. **Visualization**
   - Horizontal bar chart of product prices (color-coded by category)
   - Pie chart of items per category
   - Bar chart of stock levels
   - Scatter plot of Price vs Stock (bubble size = inventory value)
   - Category-wise inventory value chart
   - Top-5 products by total inventory value

4. **Barcode Generation**
   - Used `barcode.get_barcode_class('code128')` to get the Code128 class
   - Instantiated barcode objects with `ImageWriter()`
   - Saved each barcode PNG using `barcode_obj.save(filepath, options)`
   - Generated EAN-13 barcodes using `barcode.get_barcode_class('ean13')`
   - Applied writer options: module height/width, font size, quiet zone

5. **Product Label Creation**
   - Combined barcode image with product metadata in a styled Matplotlib layout
   - Saved individual label PNGs per product

6. **Batch Report**
   - Summarized all generated files with file sizes
   - Printed key findings and inventory insights

---

## Results

### Key Findings

| Metric | Value |
|--------|-------|
| Total Products | 12 |
| Code128 Barcodes Generated | 12 |
| EAN-13 Barcodes Generated | 6 |
| Total Inventory Value | ~$26,000+ |
| Highest Value Category | Electronics |
| Most Affordable Product | Notebook Set ($9.99) |
| Highest Stock Product | Notebook Set (500 units) |

### Barcode Formats Used

| Format | Use Case | Data Type |
|--------|----------|-----------|
| Code128 | General product IDs | Alphanumeric |
| EAN-13  | Standard retail barcodes | 12-digit numeric |

### Output Files
- `barcodes/PRD001.png` through `barcodes/PRD012.png` — Code128 barcodes
- `barcodes/EAN_*.png` — EAN-13 barcodes
- `barcodes/label_PRD*.png` — Styled product labels
- `catalog_analysis.png` — 4-panel EDA visualization
- `barcode_gallery.png` — Gallery of first 6 barcodes
- `results_summary.png` — Results summary charts

---

## Tools Used

- **Python 3.10**
- **python-barcode** — barcode image generation (Code128, EAN-13)
- **Pillow (PIL)** — image processing backend for barcode writer
- **Pandas** — product catalog data manipulation and analysis
- **NumPy** — numerical operations
- **Matplotlib** — all visualizations, charts, product labels
- **os / datetime** — file management and timestamps

### Installation

```bash
pip install python-barcode[images] pandas matplotlib numpy pillow
```

---

## Conclusion

The Barcode Generator project demonstrates how Python can be used to build a practical, real-world mini application with minimal code. Using the `python-barcode` library, we generated professional-quality scannable barcodes in two industry-standard formats (Code128 and EAN-13) for an entire product catalog in a fully automated batch process.

The project also shows the power of combining data analysis (Pandas), visualization (Matplotlib), and domain-specific libraries (python-barcode) to build end-to-end applications. The same approach can scale to thousands of products in a real retail or warehouse environment, and can be extended with features like QR codes, database integration, or web-based label printing.

---

## Author

**Hariom Anand**  
DATA.110 — Introduction to Python Programming for Machine Learning  
Summer C 2025
