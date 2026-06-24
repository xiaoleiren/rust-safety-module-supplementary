# Lab 1: From C Use-After-Free to Ownership

## Learning Objectives

By the end of this lab, you will be able to:

1. Identify use-after-free and double-free errors in C code using sanitizers
2. Translate a resource-management pattern from C to Rust
3. Explain ownership, moves, and drops as constraints on aliasing and mutation
4. Articulate why the unsafe C pattern cannot be expressed in safe Rust

## Task Overview

### Part 1: C Code Analysis (30 minutes)

You are given a short C program that demonstrates use-after-free and double-free behavior:

```
#include <stdio.h>
#include <stdlib.h>

void use_after_free_example() {
    int* ptr = (int*)malloc(sizeof(int));
    *ptr = 42;
    free(ptr);
    printf("%d\n", *ptr);  // Use-after-free
}

void double_free_example() {
    int* ptr = (int*)malloc(sizeof(int));
    free(ptr);
    free(ptr);             // Double-free
}
```

Tasks:

1. Compile the program with address sanitizer: gcc -fsanitize=address -g -o example example.c

2. Run both functions and observe the sanitizer output

3. Document what the sanitizer reports for each error type

4. Identify the exact line where the undefined behavior occurs

Part 2: Rust Translation (45 minutes)

Translate the resource-management pattern to Rust. The Rust version should:

1. Use Box<T> for heap allocation

2. Implement the same logical operations as the C code

3. Fail to compile if it tries to reproduce the unsafe pattern

Starter code:
```
fn main() {
    let ptr = Box::new(42);
    // Try to reproduce the C pattern here
    // What happens when you try to use ptr after moving it?
}
```

Tasks:

1. Attempt to write Rust code that mimics the C use-after-free pattern

2. Observe and document the compiler errors

3. Explain why each error occurs in terms of ownership and moves

4. Write a corrected version that compiles

Part 3: Contrast Report (30 minutes)

Write a short contrast report that:

1. Identifies the owner, move, drop, and invalid use points in the C code

2. Explains how Rust's ownership discipline prevents the pattern

3. Describes what the compiler error messages reveal about safety invariants

Deliverables

1. C code with sanitizer output (screenshot or text log)

2. Rust code showing the compiler errors

3. Corrected Rust code that compiles

4. Contrast report (500–800 words)

Grading Criteria

Criterion                       Weight
Sanitizer output documentation  20%
Compiler error identification   25%
Corrected Rust implementation   25%
Contrast report quality 30%
See ../rubric_templates/lab1_rubric.md for detailed rubric.

Submission Instructions
Submit a single PDF containing:

C code and sanitizer output

Rust code with compiler errors

Corrected Rust code

Contrast report

Submit via your course's submission system.

