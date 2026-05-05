# Lecture Homework Week 06 - Tuesday

For this lecture homework, you will explore and modify the Timer driver, which uses interrupts.

## Getting the Code

As with the previous lecture homework, this assignment is hosted on GitHub. You will create your own repository using the assignment repository as a template. To do this:

1. Click on "Use this template."
2. Select "Create a new repository."
3. Give your repository a descriptive name.
4. Click "Create repository."

Once created, clone the repository or open it in a GitHub Codespace to begin working.

## Adding Another Image

If you attempt to compile the program immediately after cloning, it will fail with the following error:

```bash
mkdir build
cmake -S . -B build
cmake --build build
...
arm-none-eabi-objcopy: '../image0.bmp': No such file
...
```

This occurs because, this time, no image is included in the repository. You must provide your own image (`image0.bmp`). You can think of it as the logo for your embedded operating system. Convert your chosen image to BMP format if it isn't already.

**Requirements:**

1. The image must be an appropriate size to fit on the display.
2. The image must not be a copy of `image0.bmp` from the previous lab. It should be a new, appropriate image.

### Running the code
Compile, as you have done in previous project, and run the code using QEMU:

```bash
qemu-system-arm -M versatilepb -m 128M -kernel build/timer.bin -serial mon:stdio
```

## Problem from the Textbook

For this homework assignment, you will be doing a slightly modified version of Problem 1, starting at the bottom of page 95 of the textbook.

### Problem 1

In the example program C3.1, the vector table is at the end of the `ts.s` file ([`src/start.s`](src/start.s) in this project).

**Part 1:**
In the `ts.s` file, comment out the line:
```asm
BL copy_vector
```
Recompile and run the program again. The program should not work. Explain why.

**Part 2:**
Move the vector table to the beginning of the `ts.s` file, like so:
```asm
vectors_start:
// vector table
vectors_end:
reset_handler:
```
Change the entry point in `t.ld` ([`./linker-script.ld`](./linker-script.ld) in this project) to `vectors_start`. Recompile and run the program again. It should now work. Explain why.

## What to Turn In

Ensure the following files contain your modified code and are pushed to your repository:

* `src/start.s`
* `linker-script.ld`
* `image0.bmp`

### Once Finished

**Turn in your answers to the problems above:**
1. Open the file `homework_template.docx` on your local computer and answer the questions regarding the work you did above.
2. Export the document as a PDF.
3. Add the PDF to your repository for when you check in your code in the next stop.

**Turn in your code:**
1. Commit and push your changes to GitHub.
2. Submit the assignment via Gradescope.
3. Select your repository when prompted.
