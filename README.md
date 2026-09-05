# Antenna Radiation Pattern Visualizer

## Overview

This project is a university team project developed by Computer Science students for the Faculty of Electrical Engineering. It provides a desktop application for reading antenna radiation-pattern data and turning it into visual, interactive plots.

The main focus of the project is the visualization of radiation patterns in **2D polar plots**, with an additional exploratory attempt at representing the data as a **3D surface**. The application works with antenna data files containing measurements for the H-plane and E-plane, allowing users to inspect how an antenna radiates in different directions.

## Why This Project Is Important

Antenna radiation patterns help engineers understand the direction, strength, and distribution of electromagnetic radiation. Visualizing this data makes important characteristics easier to identify, including:

- Main radiation lobes and their direction
- Side lobes and unwanted radiation
- Relative signal strength at different angles
- Differences between the H-plane and E-plane
- The effect of normalization and smoothing on the displayed pattern

Although the project was implemented by Computer Science students, it addresses a practical Electrical Engineering problem. It demonstrates how software can make specialized engineering data easier to explore, compare, and communicate.

## Main Features

- Import antenna pattern files and separate H-plane and E-plane data
- Display H-plane and E-plane radiation patterns as 2D polar plots
- View both planes separately or together
- Normalize patterns relative to their maximum value
- Smooth noisy 2D data using a Savitzky-Golay filter
- Highlight detected radiation lobes
- Customize plot colors and use standard plot navigation tools
- Navigate through recent plot states with back and forward history controls
- Save and reload project history as JSON
- Open interactive 2D and 3D Plotly visualizations in a web browser
- Experiment with a 3D radiation-pattern surface generated from the available E-plane and H-plane data

## 2D Plotting

2D plotting is the primary and most developed part of the application. Imported values are interpreted as measurements over angular positions and displayed using polar coordinates. The application can show the H-plane and E-plane independently or overlay them in a single plot for comparison.

The processing workflow includes optional normalization and smoothing. Normalization shifts each pattern relative to its maximum, which makes it easier to compare the shape of patterns even when their absolute levels differ.

## 3D Plotting Attempt

The repository also contains an experimental 3D visualization. It creates a surface from the H-plane and E-plane arrays and converts the resulting spherical-style data into Cartesian coordinates.

This 3D view is an approximation and should be considered a visualization experiment rather than a complete physical reconstruction of an antenna's true 3D radiation field. A scientifically exact 3D pattern would require measurements covering the relevant angular dimensions and a clearly defined interpolation or reconstruction method.

## Input Data

The `files/` directory contains the data used for the project, including:

- `courbe1.txt` through `courbe4.txt`: numeric radiation-pattern curves
- `.atn` files: antenna measurement files containing metadata and numeric values for the planes

The reader skips metadata and extracts numeric values. After the first numeric section, the next section is interpreted as the second plane, allowing the application to work with the provided measurement-file format.

## Project Structure

```text
Project-S4/
├── application/       Main PySide6 desktop application
│   ├── main.py        Application entry point
│   ├── controller.py  UI actions and application workflow
│   ├── logic.py       Data loading and processing model
│   └── UI_file.py      User-interface and plotting components
├── files/             Antenna data files used for plotting
├── try/               Earlier experiments and prototypes, including 3D tests
└── README.md
```

## Technologies

- Python
- PySide6 for the desktop user interface
- NumPy for numerical data handling
- SciPy for signal smoothing
- Matplotlib for embedded plots
- Plotly for browser-based interactive plots
- Pandas for reading and preparing numeric curve files

## Running the Application

Install the required Python libraries:

```bash
pip install numpy pandas scipy matplotlib plotly PySide6 PySide6-Essentials mplcursors
```

Start the main desktop application from the `application` directory:

```bash
cd application
python main.py
```

On Windows PowerShell, the same commands are:

```powershell
cd application
python main.py
```

## Academic Context

This work was completed as a university project by Computer Science students in collaboration with the Faculty of Electrical Engineering. The project combines software engineering, data processing, graphical user-interface development, and scientific visualization to support the analysis of antenna radiation measurements.

## Future Improvements

- Implement a physically validated 3D reconstruction from complete angular measurements
- Add explicit angle metadata and unit handling for each input format
- Improve validation for incomplete or irregular measurement files
- Add automated tests for parsing, normalization, smoothing, and coordinate conversion
- Provide exported images and reports for engineering documentation
