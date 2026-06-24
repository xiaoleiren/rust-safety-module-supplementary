# Lab 4 Rubric: Concurrency, Unsafe Boundaries, and What Rust Does Not Prove

| Dimension | 0 | 1 | 2 | 3 |
|-----------|---|---|---|---|
| **Problem Identification** | Misses safety/logical issues | Identifies surface issue (deadlock, unsafe) | Identifies main issue and its category | Identifies issue and boundary cases |
| **Conceptual Explanation** | Incorrect or no explanation | Treats "safe" as "correct" | Uses correct safety concepts | Explains mechanism and safety boundary |
| **Diagnostic Interpretation** | Cannot interpret guarantees | Treats compiler acceptance as proof | Connects to invariants (Send/Sync, ownership) | Distinguishes guarantee from non-guarantee |
| **Repair/Verification** | No repair or verification | Unverified suggestion | Correct fix with verification | Minimal fix plus revalidation strategy |
| **Uncertainty Awareness** (0–2) | Claims complete certainty | Generic caveat | Specific limitation identified | — |

**Total: ___ / 14**