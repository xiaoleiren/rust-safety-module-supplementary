# Lab 3: Lifetime Diagramming Worksheet

## Instructions

For each code snippet, draw a lifetime diagram showing:

1. The creation and destruction of each variable
2. The creation of each reference
3. The valid range (lifetime) of each reference
4. Any lifetime constraints between references

## Diagram Template

Use the following notation:
Variable creation: ──┐
Variable destruction: └─
Reference creation: ──┐
Reference valid range: ═════
Lifetime constraint: ═══▶═══


## Snippet A: Function Return


fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
    if x.len() > y.len() { x } else { y }
}

fn main() {
    let string1 = String::from("hello");
    let string2 = String::from("world");
    let result = longest(&string1, &string2);
    println!("{}", result);
}

Diagram:
[Draw your diagram here]

Explanation:
[Write your explanation here]

Snippet B: Struct with Reference

struct Excerpt<'a> {
    text: &'a str,
    length: usize,
}

fn main() {
    let content = String::from("This is a test");
    let excerpt = Excerpt {
        text: &content,
        length: 14,
    };
    println!("{}", excerpt.text);
}


Diagram:
[Draw your diagram here]

Explanation:
[Write your explanation here]

Snippet C: Multiple References

fn example(x: &mut Vec<i32>, y: &i32) {
    x.push(*y);
}
fn main() {
    let mut vec = vec![1, 2, 3];
    let value = &vec[0];
    example(&mut vec, value);
}

Diagram:
[Draw your diagram here]

Explanation:
[Write your explanation here]

Snippet D: Dangling Reference (Ill-Typed)

fn dangle() -> &String {
    let s = String::from("hello");
    &s
}  // s is dropped here, but reference is returned
Diagram:
[Draw your diagram here]

Explanation:
[Why would this be a dangling reference?]

Snippet E: Nested References (Challenge)

fn process<'a, 'b>(x: &'a str, y: &'b str) -> &'a str {
    // ... complex operations
}
Diagram:
[Draw your diagram here]

Explanation:
[What are the relationships between 'a and 'b?]



### 文件 6：`materials/starter_code/README.md`（独立文件）


# Starter Code Status

## During Blind Review

To maintain the anonymity of the review process, complete starter code for all four labs is not provided in this repository during the review period.

**Why?** The starter code contains original Rust code and C examples that are part of the paper's contribution. Providing them here could allow identification of the authors through coding style, comments, or prior versions.

## What Is Available

The lab handouts (`../lab_handouts/`) contain sufficient information to:

- Understand the learning objectives of each lab
- See representative code examples
- Reproduce the core tasks with original code

## After Acceptance

After the paper is accepted, this repository will be updated with:

1. Complete starter code for all four labs in the `starter_code/` directory
2. C and Rust source files for each lab
3. Sanitizer configurations (AddressSanitizer, ThreadSanitizer)
4. Sample solutions with explanations
5. Scripts for log extraction (`cargo check --message-format=json`)

## Requesting Access for Review

If chairs or reviewers require inspection of the starter code during the review process, the materials can be provided through the conference's anonymized artifact-review system.

## Current Status

materials/starter_code/
├── README.md # This file
├── lab1/ # Pending (available after acceptance)
├── lab2/ # Pending (available after acceptance)
├── lab3/ # Pending (available after acceptance)
└── lab4/ # Pending (available after acceptance)





