Below is a sample **README.md** that you can place in the root of your GitHub repository for this project. Feel free to customize sections (such as installation steps, screenshots, etc.) to suit your needs.

---

# Activity Log Prototype

This repository contains a **Python prototype application** for loading, cleaning, transforming, and analyzing online activity logs in a blended university course. The application is designed to run in **JupyterLab** under a compatible Python environment (3.7–3.10). It provides a **Tkinter**-based graphical user interface to:

1. **Load** the original CSV datasets:
   - `USER_LOG.csv`
   - `ACTIVITY_LOG.csv`
   - `COMPONENT_CODES.csv`
2. **Clean** and **transform** the data:
   - Remove rows from specific Components (e.g., *System* and *Folder*).
   - Rename columns (e.g., *User Full Name *Anonymized* → User_ID*).
3. **Merge** the datasets into a single **DataFrame**.
4. **Count** interactions by `(User_ID, Month, Component)`.
5. **Compute** key statistics (mean, median, mode) for specific components:
   - By month
   - For the entire academic period
6. **Display** correlation among different components using a heatmap.
7. **Backup** and **restore** data in **JSON** format.
8. Provide a **GUI** with appropriate feedback and error handling.

---

## Table of Contents

- [Requirements](#requirements)
- [Setup and Installation](#setup-and-installation)
- [Usage](#usage)
  - [GUI Overview](#gui-overview)
  - [Buttons and Workflow](#buttons-and-workflow)
- [Project Structure](#project-structure)
- [Key Features](#key-features)
- [Troubleshooting](#troubleshooting)
- [License](#license)

---

## Requirements

- **Python** 3.7–3.10 (64-bit recommended)
- **Anaconda** or **Miniconda** environment with:
  - `pandas`
  - `numpy`
  - `matplotlib`
  - `seaborn`
  - `tkinter` (usually included with standard Python on most systems)
- **JupyterLab** (for running the `.ipynb` notebook)

Make sure you are in a 64-bit environment if you have large datasets, to avoid memory issues when converting to JSON.

---

## Setup and Installation

1. **Clone this repository**:

   ```bash
   git clone https://github.com/YourUsername/ActivityLogPrototype.git
   cd ActivityLogPrototype
   ```

2. **Create (or activate) a conda environment**:

   ```bash
   conda create -n activity_log_env python=3.10
   conda activate activity_log_env
   ```

3. **Install required packages**:

   ```bash
   conda install jupyterlab pandas numpy matplotlib seaborn
   ```
   > `tkinter` is typically installed by default with Python on most platforms. If needed, install it separately.

4. **Launch JupyterLab** in this directory:

   ```bash
   jupyter lab
   ```

5. **Open** the provided `.ipynb` notebook (e.g. `Activity_Log_Prototype.ipynb`).

---

## Usage

### GUI Overview

The notebook defines a **Tkinter** GUI application with buttons to load, clean, merge, count, compute statistics, and visualize correlation.  

When you **run all cells** in the notebook (or the main cell that calls `run_app()`), a **Tkinter window** will pop up with a series of buttons:

1. **Load CSV Data**  
   Prompts you to select:
   - `USER_LOG.csv`
   - `ACTIVITY_LOG.csv`
   - `COMPONENT_CODES.csv`
2. **Clean/Transform**  
   - Removes rows where `Component` is `System` or `Folder`.  
   - Renames `"User Full Name *Anonymized"` → `"User_ID"`.
3. **Merge Data**  
   - Merges the three DataFrames on common columns (e.g., `User_ID`, `Component`).  
   - Creates `final_merged_df`.
4. **Count Interactions**  
   - Groups `(User_ID, Month, Component)` to count the number of interactions.  
   - Stores the result in `count_df`.
5. **Compute Stats**  
   - Creates pivoted data to compute mean, median, and mode for specified components (`Quiz`, `Lecture`, `Assignment`, `Attendance`, `Survey`) by month and for the entire term.  
   - Displays results in a message box.
6. **Show Correlation**  
   - Produces a Seaborn **heatmap** of correlation across certain components (`Assignment`, `Quiz`, `Lecture`, `Book`, `Project`, `Course`).  
   - Appears in a separate window or inline in Jupyter (depending on your environment).
7. **Save as JSON**  
   - Saves `final_merged_df` to a JSON file, preserving the latest merged data.
8. **Load from JSON**  
   - Restores a previously saved JSON file back into `final_merged_df`.

### Buttons and Workflow

A typical workflow might be:

1. **Load CSV Data**  
2. **Clean/Transform**  
3. **Merge Data**  
4. **Count Interactions** (optional if you need the `count_df` for other analysis)  
5. **Compute Stats**  
6. **Show Correlation**  
7. **Save as JSON** (or skip if you don’t need a backup)  

On a later session, you can **Load from JSON** to skip loading and merging the CSVs again.

---

## Project Structure

```
ActivityLogPrototype/
  ├─ Activity_Log_Prototype.ipynb    # Main Jupyter Notebook with the Tkinter GUI and logic
  ├─ sample_data/
  │   ├─ USER_LOG.csv
  │   ├─ ACTIVITY_LOG.csv
  │   └─ COMPONENT_CODES.csv
  ├─ README.md                       # This README
  └─ requirements.txt                # (Optional) pip or conda requirements
```

**Note**: This structure is just an example. Customize as needed.

---

## Key Features

1. **GUI-based loading** of CSV data.  
2. **Data cleaning** step removes irrelevant rows and renames columns.  
3. **Pivot** transformations to aggregate interaction counts.  
4. **Descriptive Statistics** (mean, median, mode) for each month and overall.  
5. **Correlation Analysis** with a heatmap.  
6. **JSON Backup/Restore** to manage data state across sessions.  
7. **Error Handling** with message boxes for user feedback.

---

## Troubleshooting

1. **KeyError on “Component”**  
   - Ensure your CSVs contain the correct column names (e.g., `"Component"` is spelled and capitalized consistently).  
   - Check for whitespace in column headers.

2. **Memory Issues (e.g., “failed to reserve memory block”)**  
   - Use a 64-bit Python environment.  
   - Try chunked or line-by-line JSON writing if your DataFrame is very large.  
   - Check for accidental merges that inflate the dataset size.

3. **Tkinter Not Found**  
   - Make sure Tkinter is installed (it’s typically included by default on Windows and macOS). On some Linux distributions, install `python3-tk`.

4. **Plots Not Appearing**  
   - Ensure you are running `%matplotlib inline` (or `%matplotlib notebook`) in Jupyter.  
   - Or check if a new window is opening behind other windows.

---

## License

This project is released under the [MIT License](LICENSE). You’re free to use, modify, and distribute this software as allowed by the license terms.

---

### Enjoy the Project!

Feel free to open an [issue](https://github.com/YourUsername/ActivityLogPrototype/issues) or submit a pull request if you find bugs or want to contribute enhancements. 
