# Lab 3 Rubric: Lifetimes, Aliasing, and Mutation

| Dimension | 0 | 1 | 2 | 3 |
|-----------|---|---|---|---|
| **Problem Identification** | Misses the lifetime issue | Identifies surface error | Identifies the specific lifetime/aliasing problem | Identifies the problem and why references would dangle |
| **Conceptual Explanation** | Incorrect or no explanation | Repeats "lifetime error" | Uses correct lifetime/validity concept | Explains mechanism and differentiates from runtime |
| **Diagnostic Interpretation** | Cannot interpret lifetime error | Treats output as opaque | Connects output to lifetime/validity constraint | Distinguishes compile-time lifetime from runtime duration |
| **Repair/Verification** | No repair or uses 'static | Unverified/partial fix | Correct lifetime annotation/restructuring | Minimal fix plus explanation and diagram |

**Total: ___ / 12**