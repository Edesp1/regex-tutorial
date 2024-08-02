# Regular Expression - Matching an Email

Regular expressions, often referred to as regex, are patterns used to match sequences of characters in text. They are derived from the concept of regular languages coined by mathematician Stephen Cole Kleene. Regex became widely used in the late 1960s for text pattern matching and lexical analysis. While regex can seem cryptic, it can be broken down into manageable parts to understand and write expressions effectively.

## Summary

This tutorial covers the regex expression used for matching and validating an email:

This regex pattern is useful for finding email addresses within a codebase or documents and validating email formats in forms.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)
- [Practical Examples](#practical-examples)
- [Common Pitfalls](#common-pitfalls)
- [Testing and Validation](#testing-and-validation)
- [Updating the Regex](#updating-the-regex)

## Regex Components

### Anchors

Anchors mark the start and end points of the expression:
- `^` marks the start of the string.
- `$` marks the end of the string.

### Quantifiers

Quantifiers modify the previous character to specify how many times it should be matched:
- `+` matches one or more of the preceding character.
- `{min, max}` specifies a range for the number of matches (e.g., `{2, 6}` for the domain extension length).

### OR Operator

The OR operator (`|`) is used for alternation but is not used in this specific regex. It allows matching one of several patterns.

### Character Classes

Character classes define sets of characters to match:
- `[a-z0-9_\.-]` matches lowercase letters, digits, underscores, periods, and dashes.
- `[\da-z\.-]` matches digits, lowercase letters, periods, and dashes.
- `[a-z\.]` matches lowercase letters and periods.

### Flags

Regex flags modify the behavior of the expression:
- `i`: Case-insensitive matching.
- `g`: Global search (find all matches).
- `m`: Multiline mode.
- `s`: Dotall mode (dot matches newline).
- `u`: Full Unicode support.
- `y`: Sticky mode.

The regex in this tutorial does not use flags.

### Grouping and Capturing

`()` creates groups to treat multiple characters as a single unit. The regex uses parentheses to group parts of the email address:
- `([a-z0-9_\.-]+)` matches the local part before the `@`.
- `([\da-z\.-]+)` matches the domain name before the period.
- `([a-z\.]{2,6})` matches the top-level domain (TLD).

### Bracket Expressions

`[]` define character sets:
- `[a-z0-9_\.-]`: Matches a single character from the set.
- `[a-z\.]`: Matches lowercase letters and periods.

### Greedy and Lazy Match

- **Greedy Match**: Matches as much of the string as possible.
- **Lazy Match**: Matches as little of the string as possible. 

Greedy matching can be slower as it continues until the end of the string, while lazy matching stops at the first match.

### Boundaries

`\b` matches word boundaries, ensuring the match occurs at the start or end of a word.

### Back-references

Back-references refer to a previous match within the same regex, usually specified as `\1`, `\2`, etc.

### Look-ahead and Look-behind

- **Look-ahead**: `(?=foo)` matches a position where "foo" follows.
- **Look-behind**: `(?<=foo)` matches a position where "foo" precedes.

## Practical Examples

### Matching Valid Emails
- **Matches**: `example.email@domain.com`, `user.name@sub-domain.co.uk`
- **Does Not Match**: `plainaddress`, `user@domain`

### Email Example Breakdown
- `example.email@domain.com` matches:
  - Local part: `example.email`
  - Domain: `domain`
  - TLD: `com`

## Common Pitfalls

- **International Characters**: This regex does not support international characters in email addresses or domain names.
- **Extended TLDs**: Some newer TLDs can be longer than 6 characters (e.g., `.photography`).
- **Local Part Limitations**: This regex does not handle all valid characters in the local part of the email address according to RFC standards.

## Testing and Validation

To test and validate your regex, use online tools like:
- [Regex101](https://regex101.com/)
- [Regexr](https://regexr.com/)

These tools provide explanations and allow you to test your regex against various input samples.

## Updating the Regex

For a more robust email validation, consider:
- Using libraries that follow the official RFC 5322 specification.
- Implementing additional checks in code to handle edge cases and international formats.

For example, using the `validator` library in JavaScript:
```javascript
const validator = require('validator');
console.log(validator.isEmail('example.email@domain.com')); // true
```

## Author

Eduardo Lopez: Oregon Univseristy web dev student

### Sources and References
    * [regexr](https://regexr.com/)
    * [BackRef](https://www.regular-expressions.info/backref.html)
    * [RegExpression](https://www.regular-expressions.info/wordboundaries.html)

My Github [github] https://github.com/Edesp1
