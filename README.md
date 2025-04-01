# 8×8 Shape Classifier 

This project implements a lightweight, rule-based classifier for detecting basic geometric shapes — **triangles, squares, and circles** — on an 8×8 pixel grid.

### Core Idea

The classifier uses a combination of:
- **Pixel Density** (`1s` in the grid) to estimate shape size/fill
- **Edge Count** via XOR operations between horizontal and vertical neighbors to measure contour complexity

### Classification Logic

| Shape     | Pixel Count (`1s`) | Edge Count (XORs) |
|-----------|--------------------|-------------------|
| Triangle  | ~18–30             | ~8–13             |
| Square    | ~38–50             | ~14–20            |
| Circle    | ~28–40             | >20               |

- XORs are computed for all 112 adjacent horizontal/vertical pairs
- Shapes are classified based on threshold ranges for both features

###  Features

- Aimed for a constrained environment
- interpretable logic
- bitmap input (e.g. list of 0s and 1s)

### Example Usage


shape_grid = [
    [0,0,0,0,0,0,0,0],
    [0,0,0,1,0,0,0,0],
    [0,0,1,1,1,0,0,0],
    [0,1,1,1,1,1,0,0],
    [0,0,0,0,0,0,0,0],
    ...
] 
=> 00,01,...,76,77 through inputs
=> 0, 0, 1 through outputs with the third bit referring to a triangle.


Known Issues:
I understand some of the PNGS are poor for the larger combinational logic diagrams Im looking into how to improve these.
Not all the LAYOUTs are completed Im a working on these and will post them when done.
Add diagonal edge detection


There are several ...T or ...Test files this is verification testbenches with setup DC,GND,Cap, and or Vpat basic analog blocks. These basic analog blocks I did not create they were given default to our version of Synopsys so I am not posting them. 
