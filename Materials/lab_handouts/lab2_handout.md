
# Lab 2: Borrow Checker as Feedback

## Learning Objectives

By the end of this lab, you will be able to:

1. Interpret borrow-checker diagnostics as evidence about safety invariants
2. Categorize compiler errors by the safety rule they enforce
3. Repair ill-typed Rust snippets without using `clone()` as an escape hatch
4. Explain exclusive mutability and aliasing rules in your own words

## Task Overview

### Part 1: Error Categorization (20 minutes)

You are given 8 intentionally ill-typed Rust snippets. For each snippet:

1. Run `cargo check` and capture the error message
2. Categorize the error (move/ownership, immutable vs mutable borrow, lifetime/escape, etc.)
3. Explain the safety invariant the compiler is enforcing

**Snippets** (provided in `starter/` directory):

- `snippet1.rs`: Move after borrow
- `snippet2.rs`: Mutable borrow while immutable borrow exists
- `snippet3.rs`: Multiple mutable borrows
- `snippet4.rs`: Borrow of moved value
- `snippet5.rs`: Reference outlives its referent (lifetime)
- `snippet6.rs`: Mutable borrow followed by immutable use
- `snippet7.rs`: Return reference to local variable
- `snippet8.rs`: Mixed mutable and immutable borrows in function call

### Part 2: Diagnostic Annotation (40 minutes)

For each error message, annotate it with:

1. **What the compiler says**: The exact error message
2. **What the rule is**: The Rust safety rule being enforced
3. **Why it matters**: What would happen if this were allowed (use-after-free, data race, etc.)
4. **How to fix it**: The correct repair strategy

**Annotation Template:**

=== Error: snippet2.rs ===

[Compiler Output]
error[E0502]: cannot borrow data as mutable because it is also borrowed as immutable

[Rule]
Rust enforces exclusive mutation: you cannot mutate a value while it is immutably borrowed.
This prevents data races and invalidates references.

[Why It Matters]
If mutable access were allowed while immutable references exist, the immutable reference
could see the value change unexpectedly, leading to logic errors or undefined behavior.

[Fix Strategy]
Restructure the code so that the immutable borrow ends before the mutable borrow.
Use scoping to limit the immutable borrow's lifetime, or use interior mutability (RefCell)
if the pattern requires it.


### Part 3: Repair (30 minutes)

Repair each snippet so that:

1. The code compiles
2. No `clone()` is used as a blanket escape hatch
3. The fix demonstrates understanding of the underlying rule

**Forbidden:** Using `clone()` unless absolutely necessary.

## Deliverables

1. Completed annotation worksheet for all 8 snippets
2. Repaired code for all 8 snippets
3. A 1-paragraph reflection on which error category was most challenging

## Grading Criteria

| Criterion | Weight |
|-----------|--------|
| Error categorization accuracy | 30% |
| Annotation quality | 40% |
| Repair quality | 30% |

See `../rubric_templates/lab2_rubric.md` for detailed rubric.

## Submission Instructions

Submit your annotated worksheet and repaired code files.
