# DX Spectra Converter 📉

<img width="998" height="1155" alt="Screenshot 2026-01-07 172125" src="https://github.com/user-attachments/assets/11a4da7a-aba2-496e-8663-394477093889" />

## 📝 Overview
**DX Spectra Converter** is a GUI-based tool designed to batch convert spectral data files (in `.dx` / JCAMP-DX format) into a unified CSV format. 

Unlike simple converters, this tool aligns multiple spectra onto a **single unified X-axis (Wavelength)** ensuring data integrity by using **exact matches only** (no interpolation). It also automatically detects system locale to format CSVs correctly for Excel (handling European vs. US decimal separators).

## ✨ Key Features

* **Batch Processing:** Scan directories and convert multiple `.dx` files simultaneously.
* **Unified X-Axis:** Automatically identifies all unique wavelength points across all files and aligns spectra to a master axis.
* **Data Integrity:** Uses strict exact-matching logic. If a wavelength point exists in the master axis but not in a specific file, it creates a `NaN` (empty) value rather than interpolating data.
* **Smart Formatting:**
    * Auto-detects system locale (US/UK vs. European).
    * Customizable output: supports Comma/Dot, Semicolon/Comma, and Tab/Dot formats.
    * "Excel Compatible" preset included.
* **Detailed Metadata:** Extracts header info (Title, Owner, Instrument Parameters) into a separate report.

## 🛠️ Built With
* **Python** (GUI built with `tkinter`)
* **Pandas** (Data manipulation)
* **NumPy** (Numerical operations)

## 📋 Prerequisites

You need Python installed on your system. This project relies on the following external libraries:

* `pandas`
* `numpy`

Standard libraries used: `tkinter`, `os`, `re`, `pathlib`, `threading`.

## 🔧 Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/tuo-username/dx-spectra-converter.git](https://github.com/tuo-username/dx-spectra-converter.git)
    cd dx-spectra-converter
    ```

2.  **Install dependencies:**
    ```bash
    pip install pandas numpy
    ```
    *(Note: Tkinter usually comes pre-installed with Python. If you are on Linux and get an error, install it via `sudo apt-get install python3-tk`)*.

## 💻 Usage

1.  Run the application:
    ```bash
    python dx2csv.py
    ```
2.  **Select Directory:** Click "Browse" to choose the folder containing your `.dx` files.
3.  **Select Files:** Choose which spectra you want to include in the conversion.
4.  **Choose Format:** Select your preferred CSV delimiter (e.g., Semicolon for European Excel).
5.  **Convert:** Click "Convert to CSV".

## 📂 Output

The tool generates two files in the source directory:

1.  **`unified_spectra_data.csv`**: The main data matrix.
    * Column 1: `Wavelength_nm` (Unified X-axis)
    * Columns 2+: Intensity data for each file.
2.  **`spectra_metadata.csv`**: A summary report containing metadata extracted from the `.dx` headers (Title, Date, Spectrometer settings, etc.) and coverage statistics.

## 🤝 Contributing
Contributions, issues, and feature requests are welcome!

## 📄 License
[MIT](https://choosealicense.com/licenses/mit/)
