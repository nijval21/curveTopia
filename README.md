# Curve Reconstruction Project

This project aims to fit missing parts of curves using machine learning techniques. The provided script demonstrates how to load, preprocess, visualize, and reconstruct curves from given datasets.

## Table of Contents

1. [Project Overview](#project-overview)
2. [Installation](#installation)
3. [Usage](#usage)
4. [Function Descriptions](#function-descriptions)
5. [Example](#example)
6. [License](#license)

## Project Overview

This project involves:
- **Data Loading:** Importing curve data from CSV files.
- **Data Preprocessing:** Structuring data for curve reconstruction.
- **Visualization:** Plotting the curves for inspection and analysis.
- **Curve Analysis:** Determining starting and ending points of curves.
- **Reconstruction:** Reconstructing complete curves from partial data.

## Installation

To get started with this project, ensure you have the following Python libraries installed:
- `numpy`
- `matplotlib`
- `seaborn`
- `pandas`
- `opencv-python`

You can install these libraries using `pip`:

```bash
pip install numpy matplotlib seaborn pandas opencv-python
```

## Usage

1. **Prepare Your Data:**
   - Ensure you have two CSV files containing the curve data:
     - `np_path_XYs_path`: Contains the initial curve fragments.
     - `np_path_XY2s_path`: Contains the additional fragments for reconstruction.

2. **Run the Script:**
   - Modify the `main` function call in the script to point to your dataset files.
   - Execute the script to see the visualizations and reconstruction results.

```python
if __name__ == "__main__":
    main('/path/to/frag0.csv', '/path/to/frag01_sol.csv')
```

## Function Descriptions

### `load_data(np_path_XYs_path, np_path_XY2s_path)`
Loads curve data from CSV files.

- **Inputs:**
  - `np_path_XYs_path`: Path to the CSV file with initial curve data.
  - `np_path_XY2s_path`: Path to the CSV file with additional curve fragments.
- **Outputs:**
  - Two NumPy arrays: `np_path_XYs` and `np_path_XY2s`.

### `preprocess_data(np_path_XYs, np_path_XY2s)`
Prepares the data for analysis by structuring it into lists of curves.

- **Inputs:**
  - `np_path_XYs`: NumPy array of initial curve data.
  - `np_path_XY2s`: NumPy array of additional curve fragments.
- **Outputs:**
  - Lists of curves `XY` and `XY2`, and their sizes `sz1` and `sz2`.

### `visualize_curves(XY, sz1)`
Visualizes the curves.

- **Inputs:**
  - `XY`: List of curves.
  - `sz1`: Number of initial curves.
- **Outputs:**
  - Plots each curve individually.

### `visualize_complete_curve(XY, sz1)`
Visualizes all curves in a single plot.

- **Inputs:**
  - `XY`: List of curves.
  - `sz1`: Number of initial curves.
- **Outputs:**
  - A plot showing all curves.

### `analyze_curves(XY, sz1)`
Analyzes curves to determine starting and ending points.

- **Inputs:**
  - `XY`: List of curves.
  - `sz1`: Number of initial curves.
- **Outputs:**
  - Dictionaries: `curve_num`, `partner`, and `umap` for curve analysis.

### `reconstruct_single_curve(node_sequence, umap, XY, partner)`
Reconstructs a complete curve from a sequence of nodes.

- **Inputs:**
  - `node_sequence`: List of node indices.
  - `umap`: Dictionary mapping nodes to their corresponding points.
  - `XY`: List of curves.
  - `partner`: Dictionary mapping nodes to their partner nodes.
- **Outputs:**
  - An array of reconstructed curve points.

### `euclidean_distance(point1, point2)`
Calculates the Euclidean distance between two points.

- **Inputs:**
  - `point1`: Coordinates of the first point.
  - `point2`: Coordinates of the second point.
- **Outputs:**
  - The Euclidean distance between the points.

## Example

Replace the dataset paths in the `main` function with your own dataset file paths. Run the script to visualize the curves and see the results of the reconstruction.

```python
if __name__ == "__main__":
    main('/path/to/frag0.csv', '/path/to/frag01_sol.csv')
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
