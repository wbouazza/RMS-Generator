# User Guide: RMS Generator

**Author:** Wassim BOUAZZA  
**Email:** wassim.bouazza@univ-nantes.fr

This guide provides a step-by-step walkthrough of the RMS Generator tool, from creating your first configuration to exporting massive sets of variants.

---

## Table of Contents
1. [Interface Overview](#1-interface-overview)
2. [Step 1: Creating a Base Configuration](#step-1-creating-a-base-configuration)
3. [Step 2: Customizing Rules & Setup](#step-2-customizing-rules--setup)
4. [Step 3: Understanding the Visualization](#step-3-understanding-the-visualization)
5. [Step 4: Live Preview & Upload](#step-4-live-preview--upload)
6. [Step 5: Generating Variants (Expansion)](#step-5-generating-variants-expansion)

---

## 1. Interface Overview

The tool is divided into three main sections within the Jupyter Notebook (Widget area):

1.  **Creation / Import Tab**: Where you define the layout (Families, Cells, Machines) or load an existing JSON.
2.  **Configuration & Rules**: Fine-tune specific rules for Processing Time (PT) and Setup Time (ST) for each cell.
3.  **Expansion (Variants)**: A dedicated block for generating derived configurations (adding machines).

---

## Step 1: Creating a Base Configuration

**Scenario**: You want to create a system with **3 Cells**, processing **5 Product Families**.

1.  Go to the **"Create"** tab.
2.  **Families**: Set to `5`.
3.  **Cells**: Set to `3`.
4.  **Mach/Cell**: Enter `2` (Meaning 2 machines per cell initially).
    *   *Tip: You can specify comma-separated values like `2,3,2` for different sizes per cell.*
5.  **PT Min/Max**: Set the range for processing times (e.g., `1` to `10`).
6.  Click the **Create New** button.

> **Result**: A random configuration is generated. The visualization area will show 3 boxes (Cell 1, Cell 2, Cell 3), each containing 2 machines (M1, M2...).

---

## Step 2: Customizing Rules & Setup

Once a base configuration exists, you can refine how machines behave using the **Configuration** panel below the visualization.

### Global Presets
Use the buttons at the top of the panel for quick actions:
*   **Light Setup**: Sets Setup Times (ST) to be small relative to Processing Times (PT).
*   **Heavy Setup**: Sets ST to be larger than PT.
*   **Identical PT**: Forces all machines in a cell to have the same processing speeds.
*   **Chaotic**: Randomizes rules for a "messy" real-world scenario.

### Per-Cell Fine Tuning
Click on the tabs **C1, C2, C3...** to edit specific cells:
1.  **PT Rule**: Choose logic like "Identical" (all machines same) or "Heterogeneous + Resource Dependent" (machine specific speeds).
2.  **ST Mag**: Magnitude of the setup time (e.g., `< PT`, `> PT`).
3.  **Ratio**: A multiplier to fine-tune the magnitude (e.g., 0.5 for half, 1.5 for 150%).
4.  **Buttons (Zero, Light, Heavy)**: Quick presets for that specific cell.

> **Note**: Changes here might not appear immediately if **Live Preview** is off. See Step 4.

---

## Step 3: Understanding the Visualization

Each Cell is represented by a box containing:
1.  **Geometric Shape**:
    *   **Square (PT)**: Indicates Processing Time rule (White=Identical, Purple=Heterogeneous).
    *   **Circle (ST)**: Indicates Setup Time rule (Green=Light, Orange=Heavy).
2.  **Progress Bars (New!)**:
    *   Each machine (M1, M2...) has a bar showing its **Mean** capabilities.
    *   **Gray Bar**: Mean Processing Time.
    *   **Colored Bar**: Mean Setup Time.
        *   **Green**: ST <= PT (Efficient).
        *   **Orange**: ST > PT (Setup heavy).
3.  **Stats**: Displays the generated text summary (e.g., `PT: 5.2 / ST: 2.1`).

---

## Step 4: Live Preview & Upload

*   **Live/Simulated Preview**: 
    *   When **Checked**: The visualizer shows a *simulation* of what your selected rules *would* look like. It uses random numbers on the fly.
    *   When **Unchecked**: The visualizer shows the *actual* data stored in the `current_config` object.
    *   *Tip*: This box auto-checks when you modify rules. Click **(Re)generate** to commit your rules to actual data (which unchecks the box).

*   **Uploading**:
    *   Use the **Import** tab to upload a previously saved `.json` file.
    *   The tool will automatically switch Live Preview **OFF** to show you the exact content of the uploaded file.

---

## Step 5: Generating Variants (Expansion)

This is the final step where you generate the dataset for analysis.

1.  Scroll down to the **Expansion (Variants)** section.
2.  **Add X Res**: Enter `1`.
    *   This means "Generate all possible configurations where I add exactly 1 machine to the system".
    *   *Advanced*: You can enter `2` for Level 2 (2 machines added), or `1,1,1` to enforce adding 1 machine to each cell specifically.
3.  **Click "Save to Disk"**.
    *   A dialog box will open. Select your destination folder.
4.  **Output**:
    *   The tool calculates all valid combinations.
    *   It saves the **Base** configuration in a `Level_0` folder.
    *   It saves all variants in `Level_1`, `Level_2`, etc.
    *   **All Levels**: A folder containing copies of EVERY generated file for easy batch loading.
    *   **HTML Reports**: Each variant comes with an HTML file so you can view it in a browser without this tool.
