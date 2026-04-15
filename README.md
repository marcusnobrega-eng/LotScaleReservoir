# 🌧️ Catchment-Aware LID Design Tool

**An open-source Excel–VBA tool for designing lot-scale stormwater reservoirs using catchment-scale hydrology**

This repository provides a practical implementation of a hydrologic–hydraulic modeling framework for **lot-scale Low Impact Development (LID)** design, with emphasis on **micro-reservoirs** and **micro-detention ponds** in urban catchments.

The tool was developed from the methodology presented in the paper:

> **Accounting for spatial runoff variability in LID design for urban catchments: model and software development**

Unlike conventional lot-based sizing approaches, this tool explicitly accounts for the **spatial variability of runoff generation within the catchment**, so that reservoir sizing and outlet design reflect not only the lot itself, but also its **upstream hydrologic contribution** and **position in the drainage network**.

---

## 🚀 What this tool does

This software helps engineers, researchers, and planners design lot-scale detention systems that are compatible with **catchment-scale drainage constraints**.

The model combines:

- **Rational Method** for runoff estimation and reference discharge calculation
- **SCS-CN method** for infiltration losses and event-based runoff coefficient estimation
- **PULS routing** for hydraulic propagation through the reservoir

The design framework evaluates whether a proposed reservoir:

- keeps the **outflow below the admissible reference discharge**
- delays the **outflow peak sufficiently**
- respects the **maximum allowable water depth**
- provides acceptable **storage and routing performance**

---

## 🧠 Why this software is useful

In many urban drainage designs, lot-scale reservoirs are sized using only local information such as lot area or imperviousness. That simplification can produce misleading results because two lots with the same geometry may need **different reservoir volumes and outlet structures** depending on where they are located in the catchment.

This tool addresses that problem by making the design **catchment-aware**.

That means the admissible outflow from each lot is not assumed constant across the entire basin. Instead, it depends on hydrologic factors such as:

- upstream contributing area
- time of concentration
- topographic position
- runoff response of the drainage network

---

## ✨ Main features

- Catchment-aware lot-scale reservoir design
- Excel-based workflow with guided VBA interfaces
- Hydrologic and hydraulic simulation in a single file
- Support for **prismatic reservoirs**
- Support for **micro-detention ponds**
- Support for **custom stage–storage tables**
- Outlet design with:
  - orifice
  - spillway
  - combined outlet configurations
- Sensitivity analysis for outlet sizing
- Optimization focused on **minimum feasible storage volume**
- Performance indicators for comparing design alternatives

---

## 🏗️ Modeling approach

The design workflow follows four main steps:

### 1. Catchment reference constraints
The tool estimates the admissible reference hydrograph at the lot connection point based on upstream drainage conditions.

### 2. Lot-scale runoff generation
The lot runoff response is estimated from rainfall, Curve Number, and initial abstraction using the SCS-CN approach.

### 3. Inflow hydrograph generation
The reservoir inflow hydrograph is built using the Rational Method and the lot time of concentration.

### 4. Hydraulic routing
The inflow hydrograph is routed through the proposed reservoir using the PULS method to obtain:

- outflow hydrograph
- water level variation
- peak attenuation
- time-to-peak delay

A solution is considered feasible when the hydraulic and hydrologic constraints are satisfied.

---

## 📦 About the Excel–VBA implementation

This software is implemented in **Microsoft Excel with VBA macros** and uses guided interfaces to organize the workflow.

### The workbook includes tools for:

- entering catchment parameters
- defining lot characteristics
- entering rainfall IDF parameters
- configuring hydrologic settings
- configuring hydraulic routing settings
- defining reservoir geometry
- testing outlet diameters
- running simulations
- comparing feasible alternatives
- optimizing the design

### Supported reservoir representations

The tool supports different types of storage structures, including:

- **Prismatic reservoirs**, defined from geometry and outlet characteristics
- **Micro-detention ponds**, including custom stage–storage relationships
- **Tabular stage–storage input**, for cases where volume is known as a function of water depth

### Practical note on Excel compatibility

To ensure proper operation, users should:

- use **Microsoft Excel 2013 or newer**
- **enable macros** when opening the workbook
- save the file in a **local folder with open read/write access**
- avoid running the file directly from **OneDrive, Google Drive, Dropbox, SharePoint, or other synchronized/cloud-managed folders**, as this may create file-locking, permission, or VBA execution conflicts

### Recommended setup

Before using the tool:

1. Download or clone the repository
2. Move the Excel file to a local folder on your machine
3. Make sure the folder allows normal file editing and saving
4. Open the workbook in Excel
5. Click **Enable Editing** if prompted
6. Click **Enable Content / Enable Macros**
7. Save a working copy before running simulations

---

## ⚙️ Requirements

### Software requirements

- Microsoft Excel **2013 or later**
- Macros enabled
- Windows environment recommended for full VBA compatibility

### Usage requirements

- Local folder with full read/write permissions
- Avoid cloud-sync conflict folders while running the tool
- Basic knowledge of urban drainage and detention design is recommended

---

## ▶️ How to use

### 1. Open the workbook
Launch the Excel file and enable macros.

### 2. Enter catchment data
Provide the main catchment characteristics, such as:

- total catchment area
- slope
- roughness
- main drainage length
- return period
- runoff coefficient or related hydrologic inputs
- upstream contributing area for the lot

### 3. Enter rainfall and hydrologic parameters
Provide:

- IDF/Sherman parameters
- lot area
- Curve Number
- initial abstraction assumptions
- time-step configuration
- simulation time

### 4. Define the reservoir geometry
Choose the storage type and enter:

- prismatic dimensions, or
- stage–storage table, or
- detention pond geometry

Then define the outlet devices:

- orifice diameter
- spillway elevation
- spillway type and dimensions

### 5. Run the simulation
The tool computes:

- reference hydrograph
- lot inflow hydrograph
- routed outflow hydrograph
- reservoir water depth over time

### 6. Check feasibility
The design should satisfy:

- maximum outflow constraint
- minimum peak-time constraint
- maximum water-depth constraint

### 7. Assess and optimize
Use the built-in analysis tools to:

- test commercial outlet diameters
- compare feasible designs
- identify minimum-volume solutions
- explore trade-offs between volume and outflow

---

## 📊 Performance indicators

The software includes dimensionless indicators to help compare solutions and understand performance, including metrics related to:

- peak delay
- peak attenuation
- maximum depth usage
- mass balance
- relative upstream hydrologic contribution

These indicators support both engineering judgment and design optimization.

---

## 💻 Clone the repository

Use the following command in your terminal:

```bash
git clone https://github.com/marcusnobrega-eng/LotScaleReservoir.git
```

Then enter the project folder:

```bash
cd LotScaleReservoir
```

Or run both steps together:

```bash
git clone https://github.com/marcusnobrega-eng/LotScaleReservoir.git && cd LotScaleReservoir
```

---

## 📌 Important usage notes

- This is an **Excel–VBA application**, not a standalone executable
- **Macros must be enabled** for the interfaces and calculations to work
- Use **Microsoft Excel 2013 or newer**

Running the workbook inside synchronized folders (e.g., OneDrive, Google Drive, Dropbox) may cause:

- autosave conflicts
- file locking
- permission issues
- unstable VBA behavior

👉 For best stability, always work on a **local copy stored in a folder with full read/write access**

---

### ⚠️ Limitations

The current implementation follows the assumptions of the underlying model, including:

- lumped hydrologic representation
- spatially uniform rainfall for the design event
- simplified time-of-concentration estimation
- main-channel-focused travel-time representation

These assumptions make the tool practical and accessible, but results should be interpreted within the scope of conceptual urban drainage design.

---

### 🙌 Citation

If you use this software in research or practice, please cite:

> Gomes Júnior, M. N. (2026). *Accounting for spatial runoff variability in LID design for urban catchments: model and software development*. Brazilian Journal of Water Resources.
