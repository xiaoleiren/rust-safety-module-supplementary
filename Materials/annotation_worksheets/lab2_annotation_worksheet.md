# Lab 2: Diagnostic Annotation Worksheet

## Instructions

For each compiler error, complete the following template.

## Template

=== Error: [filename.rs] ===

[1. COMPILER OUTPUT]
Paste the exact compiler error message here.

[2. ERROR CATEGORY]

Move/ownership

Immutable vs mutable borrow

Lifetime/escape

Trait bound/concurrency

Ordinary type error

Syntax/build issue

[3. WHAT THE COMPILER SAYS]
In your own words, what is the compiler telling you?

[4. WHAT THE RULE IS]
What Rust safety rule is being enforced? (e.g., "exclusive mutation prevents data races")

[5. WHY IT MATTERS]
What would happen if this were allowed? (e.g., use-after-free, data race, dangling reference)

[6. FIX STRATEGY]
How should this be fixed? What is the conceptual repair?


## Example

=== Error: snippet2.rs ===

[1. COMPILER OUTPUT]
error[E0502]: cannot borrow data as mutable because it is also borrowed as immutable

[2. ERROR CATEGORY]
[X] Immutable vs mutable borrow

[3. WHAT THE COMPILER SAYS]
The compiler is telling me that I'm trying to modify data while there is an active
immutable reference to it.

[4. WHAT THE RULE IS]
Rust enforces exclusive mutation: you cannot mutate a value while it is immutably borrowed.
This prevents data races and invalidates references.

[5. WHY IT MATTERS]
If mutable access were allowed while immutable references exist, the immutable reference
could see the value change unexpectedly, leading to logic errors or undefined behavior.

[6. FIX STRATEGY]
Restructure the code so that the immutable borrow ends before the mutable borrow.
Use scoping to limit the immutable borrow's lifetime, or use RefCell if the pattern
requires interior mutability.


## Snippets to Annotate

1. `snippet1.rs` — Move after borrow
2. `snippet2.rs` — Mutable borrow while immutable borrow exists
3. `snippet3.rs` — Multiple mutable borrows
4. `snippet4.rs` — Borrow of moved value
5. `snippet5.rs` — Reference outlives its referent
6. `snippet6.rs` — Mutable borrow followed by immutable use
7. `snippet7.rs` — Return reference to local variable
8. `snippet8.rs` — Mixed borrows in function call

