---
name: lpic
lesson: "18"
topic: regex, find files by regular expression
number: "18"
---
- single `.` --> everything
- some `...` --> each point means of 1 character ---> `amir` --> `..` --> am
- `*` --> all
- `^a` --> a at first of each line or string
- `a$` --> a string at the end of each line
- `a*` ---> all words with start with a
- `[abx]` ---> any word which has one of this character
- `[a-z]`---> from a to z,  any words which has it
- `[A-Z]` ---> like above but for upper-case
- `[0-9]` ---> any number ---> used for digit
- `[x]{2}` --> any words which has 2 x
- `[x]{1-10}` ---> like above but has one or more than 1 and less than 10 x
- `[x]+` --> zero or 1 of x
- `/d` ---> for digit
- `[^x]` ---> any word which has no x
- `.*` ---> all
- `?` ---> maby it be maby not ---> `[amir]10?` ---> matches `amir` and `amir10`
- `|` ----> like in programming,  means `OR` ===> `([a-z]|[A-Z])`
### character classes
`\s` ----> any space or tab
`\s` ---> match any non-whitespace
`\w` ---> match any string character
`\W` ---> match any non-string
`\d` ---> match any digit
`\D` ---> match any non-digit
`\b` ---> matches any word boundries
`\B` ---> matches any non-word boundries
