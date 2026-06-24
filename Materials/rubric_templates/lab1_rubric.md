## materials/rubric_templates/lab1_rubric.md


# Lab 1 Rubric: From C Use-After-Free to Ownership

| Dimension | 0 | 1 | 2 | 3 |
|-----------|---|---|---|---|
| **Problem Identification** | Misses the issue entirely | Identifies surface symptom (e.g., "program crashes") | Identifies main safety issue (use-after-free/double-free) | Identifies main safety issue and boundary cases |
| **Conceptual Explanation** | Incorrect or no explanation | Repeats sanitizer output | Uses correct Rust concept (ownership, move, drop) | Explains mechanism and why the C pattern is impossible in safe Rust |
| **Diagnostic Interpretation** | Cannot interpret sanitizer/compiler output | Treats output as opaque | Connects compiler error to ownership invariant | Distinguishes compile-time prevention from runtime detection |
| **Repair/Verification** | No repair or incorrect repair | Unverified/partial fix | Correct Rust implementation with explanation | Minimal fix plus explanation of why it works |

**Total: ___ / 12**