# Selection sort in MIPS assembly

![MIPS](https://img.shields.io/badge/MIPS-Assembly-6E4C9B?style=flat)
![MARS](https://img.shields.io/badge/Simulator-MARS%20%7C%20QtSpim-2C3E50?style=flat)
![License](https://img.shields.io/badge/License-CC%20BY--NC%204.0-0a2c46?style=flat)

Sorting is one line in Python. In assembly you manage every register, address and loop counter yourself. I wrote selection sort in MIPS for a university course to see what a "simple" algorithm costs at the lowest level. It sorts either a list of integers or the characters of a string.

## How selection sort works

Walk through the list, find the smallest item in the part that isn't sorted yet, and swap it to the front of that part. Repeat until nothing is left. It always does about n²/2 comparisons, which is slow for big lists but easy to get right.

## What's in the repo

| File | What it does |
|---|---|
| `src/SelectionSort.asm` | Asks whether you want to sort integers or characters, then does it |
| `src/SelectionSort_Int.asm` | Integers only |
| `src/SelectionSort_Char.asm` | Characters only |

**Integers:** you enter the array size, then one number per line. The numbers are stored on the stack, four bytes each.

**Characters:** you type a string, and its characters are sorted in place by their ASCII codes.

Either way, the program prints the sorted result, with the prompts shown in the console.


## Caveats

- **Any menu choice other than 1 or 2 sorts integers.** There's no "invalid choice" check, so the code falls through to the integer sort.
- **The integers are written above the stack pointer** without moving it first. It works in the simulator, but it isn't how stack space is meant to be claimed.
- **Uppercase sorts before lowercase,** because the sort compares ASCII codes.

## How to run

1. Download [MARS](https://computerscience.missouristate.edu/mars-mips-simulator.htm) (needs Java) or [QtSpim](https://spimsimulator.sourceforge.net/).
2. Open one of the `.asm` files in `src/`.
3. Assemble it, run it, and type your input in the console.

## What I'd like to do next

Fix the menu check, and write insertion sort the same way to compare instruction counts in MARS.
