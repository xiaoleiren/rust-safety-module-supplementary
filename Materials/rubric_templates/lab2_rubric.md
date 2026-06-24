# Lab 2 Rubric: Borrow Checker as Feedback

| Dimension | 0 | 1 | 2 | 3 |
|-----------|---|---|---|---|
| **Problem Identification** | Misses the error type | Identifies surface error ("compiler says no") | Identifies the specific borrow/ownership rule violated | Identifies the rule and its safety purpose |
| **Conceptual Explanation** | Incorrect or no explanation | Paraphrases compiler output | Uses correct Rust concept (borrow, move, lifetime) | Explains mechanism and why the invariant matters |
| **Diagnostic Interpretation** | Cannot interpret error message | Treats output as opaque | Connects output to invariant | Distinguishes compile-time guarantee from runtime behavior |
| **Repair/Verification** | No repair or uses clone as escape | Unverified/partial fix | Correct repair without clone | Minimal fix plus explanation |

**Total: ___ / 12**