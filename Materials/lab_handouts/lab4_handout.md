
# Lab 4: Concurrency, Unsafe Boundaries, and What Rust Does Not Prove

## Learning Objectives

By the end of this lab, you will be able to:

1. Distinguish memory safety from deadlock freedom and logical correctness
2. Identify the boundary where Rust's guarantees stop
3. Audit unsafe code for contract violations
4. Evaluate the safety of a wrapper around unsafe/FFI code

## Task Overview

### Part 1: Concurrency Audit (45 minutes)

You are given a concurrent Rust program that uses:

- `Arc<Mutex<Vec<i32>>>` for shared mutable state
- Multiple threads with different lock acquisition orders
- Channels for thread communication
- A deliberately introduced deadlock scenario

**Audit Requirements:**

For each of the following properties, determine whether Rust guarantees it:

| Property | Rust Guarantees? | Explanation |
|----------|------------------|-------------|
| No data races | Yes | Mutex ensures exclusive access |
| No deadlocks | No | Rust does not prevent lock ordering issues |
| No use-after-free | Yes | Ownership discipline |
| Thread safety (Send/Sync) | Yes | Trait bounds enforce Send/Sync |
| Logical correctness | No | Compiler does not verify semantics |
| No memory leaks | No | Rust allows memory leaks in safe code |

**Tasks:**

1. Run the program and observe the deadlock
2. Identify the lock order that causes the deadlock
3. Document how the compiler enforces `Send` and `Sync` bounds
4. Explain why Rust cannot prevent deadlock

### Part 2: Unsafe Boundary Audit (45 minutes)

The program includes a deliberately introduced `unsafe` or FFI boundary:

```
use std::ffi::CString;
use std::os::raw::c_char;

extern "C" {
    fn libc_free(ptr: *mut c_char);
}

/// SAFETY: Assumes the pointer is valid and allocated by libc malloc
pub unsafe fn free_c_string(ptr: *mut c_char) {
    libc_free(ptr);
}
```

Audit Requirements:

1. Identify what makes the unsafe block unsafe

2. Evaluate the safety contract (preconditions and postconditions)

3. Identify what the compiler can and cannot check

4. Propose verification methods for the contract

Tasks:

1. Document the safety contract for free_c_string

2. Identify potential violations of the contract

3. Propose runtime assertions where possible

4. Consider alternatives to raw libc::free

Part 3: Safe but Incorrect (30 minutes)
The program also contains safe Rust code that is logically incorrect:

1. A deadlock that compiles with no warnings

2. A logical error that produces wrong results

3. A resource leak that Rust allows

Tasks:

1. Identify each issue

2. Explain why Rust compilers do not catch it

3. Propose testing or verification methods to catch it

Deliverables

1. Concurrency audit report (Part 1)

2. Unsafe boundary audit with contract analysis (Part 2)

3. Safe-but-incorrect analysis (Part 3)

4. Reflection on "what Rust does NOT prove" (1 page)

Grading Criteria
Criterion                   Weight
Problem identification      20%
Conceptual explanation      25%
Diagnostic interpretation   20%
Repair/verification         20%
Uncertainty awareness       15%
See ../rubric_templates/lab4_rubric.md for detailed rubric.

Submission Instructions
Submit your audit reports and reflection as a single PDF.


