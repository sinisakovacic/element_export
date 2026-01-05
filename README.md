# element_export
element_export is a lightweight SketchUp extension for exporting selected Groups and Components into a clean CSV file containing dimensions, thickness, quantity, and edge‑banding information — perfect for creating accurate woodworking cut‑lists.

Designed for real‑world carpentry workflows, it automatically detects part orientation, materials, and multi‑side edge banding, making it ideal for cabinetmaking, furniture design, and CNC preparation.

## 📌 Overview
This extension exports selected SketchUp Groups and Component Instances into a structured CSV file suitable for:
+ Cut‑list optimizers
+ CNC machining workflows
+ Excel / Google Sheets
+ Carpentry production planning
The exporter automatically detects:
+ Part label (from Tag/Layer)
+ Length, width, thickness (auto‑sorted)
+ Edge banding on all four sides
+ Materials applied to faces (not just components)
+ Quantity of identical parts (automatic counting)

## ✨ Features
### Automatic Dimension Detection
The script reads the bounding box of each selected object and determines:
1. Thickness → smallest dimension
2. Width → middle dimension
3. Length → largest dimension
This ensures consistent orientation regardless of how the part is drawn.

### Smart Material Detection (3‑Level Scan)
Materials are detected from:
1. Component instance
2. Component definition
3. Individual faces inside the component
This is essential because many users apply edge‑banding materials directly to faces.

### Multi‑Side Edge Banding Detection
If different faces have different materials, the script detects all of them.
Banding rules (exact material name match):

| **Material Name**  | **Banding Side** |
| ------------------ | ---------------- |
|     Color A01   	 |    Left (eb1)    |
|     Color A02	     |    Right (eb2)   |
|     Color A03	     |    Right (eb3)   |
|     Color A04	     |    Right (eb4)   |

Multiple sides can be banded on the same part.

### Tag‑Based Naming
Part names are taken from the Tag (Layer) assigned to the object.
Fallbacks:
1. Component instance name
2. Component definition name
3. "Unnamed"

### Automatic Counting of Identical Parts
Identical parts (same label, dimensions, and edge banding) are automatically grouped and counted.
This produces a clean, production‑ready CSV without duplicates.

### Sorted Output
The final CSV is sorted by:
Thickness (deb) — descending
Length — descending
Width — descending
Perfect for carpentry workflows and cut‑list optimizers.

### Clean CSV Output
The exported CSV contains:
```
name,deb,length,width,pices,eb1,eb2,eb3,eb4
```

## 📁 Example Output
```
name,length,width,thickness,eb_l,eb_r,eb_t,eb_b
Front,18,720,396,2,x,x,,
Side,18,720,560,2,,,,
Shelf,16,720,560,1,x,,x,x
```

## 🛠 Installation
1. Copy the .rb file into your SketchUp Plugins folder:
+ Windows:  
C:\Users\<username>\AppData\Roaming\SketchUp\SketchUp 20xx\SketchUp\Plugins

+ macOS:  
~/Library/Application Support/SketchUp 20xx/SketchUp/Plugins
3. Restart SketchUp.
4. The extension will appear under:
Extensions → element export

## 🚀 Usage
1. Select one or more Groups or Components in SketchUp.
2. Go to Extensions → element export.
3. Choose a location to save dimenzije.csv.
4. Import the CSV into your cut‑list optimizer or CNC workflow.

## 🤝 Contributing
Pull requests and feature suggestions are welcome.
