# Hex Value Regex Tutorial

## Summary

As a full stack web development student I wanted to create a tutorial explaing the breakdown of this Hec Value Regex `/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`.
In this tutorial I will explain all the components that make up this regex.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)

## Regex Components

### Anchors

Anchors do not match any character at all instead they match the position before, after, or between chracters. Both `^` and `$` are considered anchors.

- `^abc$`
  - `^` This signifies a string that begins with characters that follow it.
    There are two formats of this: - An exact string match such as `^Hello`, where `"Hello"` or `"Hello Marta"`. However, regex is case sensitive so `"hello"` and `"hello Marta"` would not match. - A range of possible matches.
  - `$` This signifies a string that ends with characters that precede it. It has the same two formats as `^`

In our tutorial of "Matching a Hex Value" regex, the string must start or end with `#?` and `([a-f0-9]|[a-f0-9])`. We have excluded `{6}` and `{3}` because these are special components called quantifiers which I will talk a out later in the tutorial.

### Quantifiers

Quantifiers set the limits of the string that your regex matches or an individual section of the string. They are inherently greedy which means they match as many occurences of particular patterns as possible.

- `*` Matches a pattern zero or more times
- `+` Matches the pattern one or more times
- `?` Matches the pattern zero or one time
- `{}` Curly brackets can provide three different ways to set limits for a match:
  - `{ n }` Matches the pattern exactly `n` number of times
  - `{ n, }` Matches the pattern at least `n` number of times
  - `{ n, x }` Matches the pattern from a minimum of `n` number of times to a maximum of `x` number of times

These quantifiers can be made lazy by adding the `?` symbol after it, meaning that it will match as few occurances as possible.

In our "Matching a Hex Value" regex, quantifiers make an appearnce in a few instances.

- We firsts have the quantifier `?` in `#?` which means that it matches the preceding character `#` zero or one time.
- We also have two instances of curly brackets. First we have `{6}` which looks for exactly 6 characters and then `{3}` which looks for exactly 3 characters.

### OR Operator

Using the OR Operator `|`, an expression like [abc] can be written as [a|b|c].
In our Hex match regex we have two expressions in the group `([a-f0-9]{6}|[a-f0-9]{3})`, `[a-f0-9]{6}` and `[a-f0-9]{3}`. This means that our regex will match either of the two expressions.

### Character Classes

A character class in regex defines a set of chracters, which can occur in an input string to fulfill a match.
Here are some common character classes:

- `.` Matches any character except the newline character `\n`
- `\d` Matches any Arabic numeral digit.
- `\w` Matches any alphanumeric character from the basic Latin alphabet, including the underscore ` (_)` This class is equivalent to the bracket expression `[a-f0-9]`
- `\s` Matches a single whitespace character, including tabs and line breaks.

In our regex we have one characte class that is repeated twice `[a-f0-9]`. A character class will match any character enclosed in brackets. In our character class we have two ranges: `a-f` and `0-9`. That means it will match any character a through f and any number 0 through 9. Remeber that regex is case sensitive so it will only match lowecase letters a through f.

### Grouping and Capturing

More complicated regexes use grouping constructs to check multiple parts of a string by breaking these sections up. You primarily group a section by using parentheses `()`.

In our "Matching a Hex Value" regex parentheses are used but not to break up the expression into sections.

### Bracket Expressions

Anything inside a set of square brackets `[]` represents a range of characters that we want to match. In our "Matching a Hex Value" regex we have the same bracket expression `[a-f0-9]` repeated twice. THe breakdown is as follows:

- `[a-f]` The string can contain any lowercase letter between a-f.
- `[0-9]` The string can contain any number 0-9

### Greedy and Lazy Match

- 'Greedy' means matching the longest possible string. A Greedy quantifier tells the engine to match as many instances of its quantified token or subpattern as possible. This behavior is called greedy.

- 'Lazy' means matching the shortest possible string. A lazy quantifier tells the engine to match as few of the quantified tokens as needed. As you'll see in the table below, a regular quantifier is made lazy by appending a ? question mark to it.

In the beginning of our "Matching a Hex Value" regex we see `#?` which is made lazy by adding the `?`

## Author

[Marta Schwarz](https://github.com/MartaS333)
