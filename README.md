# Tu-Maze test

**Tu-Maze (Test Sandbox)** is a generic, template repository of the [Tu-Maze project](https://github.com/Tugamer89/Tu-Maze), completely rewritten using **SFML 3.0** and **GLM**.

This specific test configuration focuses on implementing a manual, software-based perspective projection mechanism (`x' = x/z`, `y' = y/z`) to render a real-time, rotating 3D wireframe cube directly onto a 2D viewport. The core rendering engine features strict C++20 standard compliance, real-time animation clock tracking, and an automated multi-stage compilation framework.

From stage 3 this project extends [FCG](https://github.com/Tugamer89/FCG) [Lab7](https://github.com/Tugamer89/FCG/tree/main/Lab7) with [SFML ImGui](https://github.com/SFML/imgui-sfml).

---

## Installation & Build Instructions

### Prerequisites

Ensure you have Git, CMake (v3.5 or higher), and a C++20 compliant compiler (such as GCC 15+, Clang, or MSVC) installed on your system.

### 1. Clone the Repository

```bash
git clone https://github.com/tugamer89/tu-maze_test.git
cd tu-maze_test
```

### 2. Standalone Development Mode

To compile and run the main branch of the project in standalone development mode, use the following standard CMake commands from the root directory:

#### Configure the Project

```bash
cmake -B build -G Ninja -DCMAKE_BUILD_TYPE=Release
```

*(Note: You can omit `-G Ninja` if you prefer to use your system's default build generator like Make or MSBuild).*

#### Compile the Project

```bash
cmake --build build --config Release
```

Upon successful compilation, the compiled standalone binary along with its assets will be automatically placed in the centralized binary output folder: `build/bin/`.

#### Run the Application

```bash
./build/bin/cube
```

---

## Managing and Compiling Project Stages (Export Workflow)

This repository tracks the evolutionary milestones of the project using semantic versioning (SemVer) Git tags. A centralized automation utility script, `export.sh`, handles checking out historic milestones, filtering configuration configurations, and compiling them into a single parallelized collection.

### 1. Exporting Milestones (Stages)

To extract all tagged minor versions of the project into individual modular subdirectories (`FCG_Stages/Stage_01`, `FCG_Stages/Stage_02`, etc.) and automatically generate a unified wrapper `CMakeLists.txt`, execute:

```bash
./export.sh x
# or: ./export.sh export
```

This script parses your Git tag history, safely copies tracked source files for each valid release version, and returns your workspace seamlessly to your active development branch.

### 2. Centralized Multi-Stage Compilation

Once exported, you can compile all evolutionary stages simultaneously in parallel through a single unified build tree by running:

```bash
./export.sh c
# or: ./export.sh compile
```

Alternatively, you can chain both the export and the compilation pipelines sequentially in one single command:

```bash
./export.sh a
# or: ./export.sh all
```

### 3. Running an Independent Stage Executable

Once compiled via the centralized multi-stage workspace, the independent executables for each specific milestone are isolated inside the build directory:

```bash
# To run Stage 1
cd FCG_Stages/build/bin/Stage_01
./tu-maze  # I apologize for the name mismatch, it was a bad version of CMakeLists.txt

# To run Stage 2
cd ../Stage_02
./cube

# To run Stage 3
cd ../Stage_03
./tu-maze_test resources/meshes/[Mesh Name].off

# And so on...
```

## User Interface Controls & Documentation

### Stage 1 (v0.1.x)

#### Keyboard Controls

* **`Escape`**: Closes the application and shuts down the rendering loop immediately.

#### Mouse Controls

* **`Window Close Button (X)`**: Clicking the native OS window close button terminates the program safely.
* *Note: No interactive in-window mouse controls are implemented in this stage.*

### Stage 3 (v0.3.x)

#### Keyboard Controls

* **`Escape`**: Closes the application and shuts down the rendering loop immediately.
* **`G`**: Use Gouraud shaders.
* **`P`**: Use Phong shaders.
* **`F`**: Use Flat shaders.
* **`C`**: Use Normal shaders.
* **`N`**: use normal camera view.
* **`T`**: use telescopic camera view.
* **`W`**: use wideangle camera view.

#### Mouse Controls

* **`Window Close Button (X)`**: Clicking the native OS window close button terminates the program safely.
* **`Left Mouse Button` while dragging**: rotate the object.
* **`Left Mouse Button` + `Left Control` while dragging**: zoom.
* **`Left Mouse Button` + `Left Alt` while dragging**: mvoe the object.

## Credits & Asset Attributions

### Project Inspiration & Algorithms

* **3D Perspective Projection Logic**: Core perspective transformation framework (based on the $x' = \frac{x}{z}$ formula) inspired and readapted from Tsoding's YouTube video [*"One Formula That Demystifies 3D Graphics"*](https://www.youtube.com/watch?v=qjWkNZ0SXfo).
* **Basecode for Stage 3**: Template from [FCG](https://github.com/Tugamer89/FCG) [Lab7](https://github.com/Tugamer89/FCG/tree/main/Lab7)

### Documentation & Support

* **Documentation Assistance**: Structured, refined, and generated with the assistance of [Gemini](https://gemini.google.com/).
