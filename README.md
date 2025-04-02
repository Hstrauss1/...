NOTE: This was made using Synopsys Custom Compiler as part of an academic environment.  
> I am not fully aware of the licensing terms or distribution rules associated with this compiler.  
> If you are affiliated with Synopsys or have information about usage rights, please feel free to reach out. My email will be at the bottom.


I used ***SAED_PDK_90*** for the nmos and pmos instances. I specifically used nmos_4t and pmost_4t versions with 0.4um and 1.2um widths and 0.1um lengths respectively. designed for a 1.2v standard.

# 8×8 Shape Classifier 

<img width="1010" alt="determine" src="https://github.com/user-attachments/assets/eaefc91e-1ef5-4324-b612-54ef5ff80f5e" />


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

### Example Usage #2

This is pulled from DetermineTest as a circle test.

Visualized Input:

<img width="756" alt="Screenshot 2025-03-28 at 5 25 49 PM" src="https://github.com/user-attachments/assets/6b932155-d22c-409d-b8c3-89d437752ef5" />

Transient Output:

<img width="1512" alt="Screenshot 2025-03-28 at 5 32 52 PM" src="https://github.com/user-attachments/assets/f1886892-f899-4374-8011-e1f882a5d404" />


Known Issues:
I understand some of the PNGS are poor for the larger combinational logic diagrams Im looking into how to improve these.

Not all the LAYOUTs are completed Im working on these and will post them when done.

Add diagonal edge detection


There are several ...T or ...Test files this is verification testbenches with setup DC,GND,Cap, and or Vpat basic analog blocks. These basic analog blocks I did not create they were given default to our version of Synopsys so I am not posting them. 





Contact me @ Hstrauss@scu.edu
