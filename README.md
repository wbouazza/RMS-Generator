# RMS Configuration Generator

**Author:** Wassim BOUAZZA  
**Email:** [wassim.bouazza@univ-nantes.fr](mailto:wassim.bouazza@univ-nantes.fr)

## Overview

The **RMS Generator** is a powerful Jupyter Notebook tool designed for the modeling, generation, and analysis of Reconfigurable Manufacturing System (RMS) configurations. It allows researchers and engineers to create complex system architectures, apply specific configuration rules, visualize resource capabilities, and systematically generate system variants for analysis.

## Key Features

*   **Dynamic Configuration Generation**: Create core RMS architectures by defining the number of cells, families, and machines per cell.
*   **Flexible Rule Application**: distinct rules for Processing Times (PT) and Setup Times (ST) assignment:
    *   *Identical*: Uniform values across resources/families.
    *   *Family Dependent*: Values vary by product family.
    *   *Resource Dependent*: Values vary by machine.
    *   *Heterogeneous*: Complete randomization.
*   **Visual Analytics**: 
    *   Interactive HTML/SVG visualization of cells and resources in real-time.
    *   Color-coded indicators for efficiency (Setup Time vs Processing Time).
    *   Detailed progress bars showing mean PT/ST per resource.
*   **Variant Expansion Engine**: 
    *   Combinatorial generation of system variants by adding resources (machines) to existing cells.
    *   Generates "Level X" variants (adding X machines relative to base).
    *   Automated duplicate detection and pruning.
*   **Export Capabilities**:
    *   Batch export of configurations to JSON.
    *   Automatic generation of visual HTML reports for each variant.
    *   Structured file organization (Base -> Level 0, Variants -> Level 1..N).

## Prerequisites

*   Python 3.8+
*   Jupyter Notebook / Lab
*   **Dependencies**:
    *   `ipywidgets`
    *   `tkinter` (usually included with Python)
    *   `matplotlib` (optional, for advanced plotting)

## Quick Start

1.  Launch the notebook: `jupyter notebook RMS_Generator.ipynb`
2.  Run all cells to initialize the interface.
3.  Use the **Configuration** tab to define your system parameters (Families, Cells, etc.).
4.  Click **Create New** to generate a base system.
5.  Use the **Expansion** section to generate and save variants (Save to Disk).

## License

This project is developed for academic and research purposes at Université de Nantes.
