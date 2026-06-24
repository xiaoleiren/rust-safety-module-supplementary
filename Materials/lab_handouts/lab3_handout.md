# Lab 3: Lifetimes, Aliasing, and Mutation

## Learning Objectives

By the end of this lab, you will be able to:

1. Draw lifetime/validity diagrams for reference relationships
2. Explain why a proposed reference would dangle if accepted
3. Repair lifetime errors in function signatures and struct definitions
4. Distinguish lifetime as a compile-time constraint from runtime duration

## Task Overview

### Part 1: Lifetime Diagramming (30 minutes)

For each of the following code snippets, draw a lifetime diagram showing:

1. The creation and destruction of each variable
2. The creation of each reference
3. The valid range (lifetime) of each reference
4. Any lifetime constraints between references

**Snippets:**

```
// Snippet A: Function return
fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
    if x.len() > y.len() { x } else { y }
}

// Snippet B: Struct with reference
struct Excerpt<'a> {
    text: &'a str,
    length: usize,
}

// Snippet C: Multiple references
fn example(x: &mut Vec<i32>, y: &i32) {
    // ... operations
}
```

Part 2: Ill-Typed Lifetime Examples (30 minutes)
Analyze examples where references escape their intended valid region:

1. Function returning reference to parameter that outlives the return

2. Struct containing references with invalid lifetime bounds

3. Nested references with conflicting lifetime requirements

For each example, provide:

1. The compiler error message

2. A diagram showing why the reference would dangle

3. A correct repair

Part 3: Transfer Task (30 minutes)
Solve the following previously unseen lifetime problem:
```
// Complete this function signature and body so that it compiles
// The function should take two string references and return the longer one
// but with the lifetime constraints correctly specified.

fn choose_longer(/* ??? */) -> /* ??? */ {
    // Implementation
}
```
Requirements:

The function must compile

Your solution must include a written explanation of the lifetime constraints

You cannot use 'static as an escape hatch

Deliverables

1. Lifetime diagrams for Part 1

2. Annotated error analysis for Part 2

3. Correct solution for the transfer task with explanation

Grading Criteria
Criterion                   Weight
Lifetime diagram accuracy   30%
Error analysis depth        35%
Transfer task solution      35%
See ../rubric_templates/lab3_rubric.md for detailed rubric.

Submission Instructions
Submit your diagrams, analysis, and transfer task solution as a single PDF.

