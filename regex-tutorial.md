# Regex Tutorial

This tutorial serves as a resource for regular expressions.

## Summary

A regular expression (shortened as regex or regexp; sometimes referred to as rational expression is a sequence of characters that specifies a search pattern in text. This tutorial serves as a resource for regular expressions.

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

## Regex Components

### Anchors

Anchors are regex tokens that don't match any characters but that say or assert something about the string or the matching process.

^The        matches any string that starts with The ->
end$        matches a string that ends with end
^The end$   exact string match (starts and ends with The end)
roar        matches any string that has the text roar in it


### Quantifiers

Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found.

abc*        matches a string that has ab followed by zero or more c ->
abc+        matches a string that has ab followed by one or more c
abc?        matches a string that has ab followed by zero or one c
abc{2}      matches a string that has ab followed by 2 c
abc{2,}     matches a string that has ab followed by 2 or more c
abc{2,5}    matches a string that has ab followed by 2 up to 5 c
a(bc)*      matches a string that has a followed by zero or more copies of the sequence bc
a(bc){2,5}  matches a string that has a followed by 2 up to 5 copies of the sequence bc

### OR Operator

a(b|c)     matches a string that has a followed by b or c (and captures b or c) ->
a[bc]      same as previous, but without capturing b or c

### Character Classes

A character class is a set of characters enclosed within square brackets. It specifies the characters that will successfully match a single character from a given input string.

\d         matches a single character that is a digit -> 
\w         matches a word character (alphanumeric character plus underscore) -> 
\s         matches a whitespace character (includes tabs and line breaks)
.          matches any character ->

### Flags

g (global) does not return after the first match, restarting the subsequent searches from the end of the previous match
m (multi-line) when enabled ^ and $ will match the start and end of a line, instead of the whole string
i (insensitive) makes the whole expression case-insensitive (for instance /aBc/i would match AbC)

### Grouping and Capturing

a(bc)           parentheses create a capturing group with value bc ->
a(?:bc)*        using ?: we disable the capturing group ->
a(?<foo>bc)     using ?<foo> we put a name to the group ->

### Bracket Expressions

[abc]            matches a string that has either an a or a b or a c -> is the same as a|b|c -> 
[a-c]            same as previous
[a-fA-F0-9]      a string that represents a single hexadecimal digit, case insensitively -> 
[0-9]%           a string that has a character from 0 to 9 before a % sign
[^a-zA-Z]        a string that has not a letter from a to z or from A to Z. In this case the ^ is used as negation of the expression ->

### Greedy and Lazy Match

'Greedy' means match longest possible string.

'Lazy' means match shortest possible string.

The quantifiers ( * + {}) are greedy operators, so they expand the match as far as they can through the provided text.

### Boundaries

\babc\b          performs a "whole words only" search ->
\Babc\B          matches only if the pattern is fully surrounded by word characters ->

### Back-references

([abc])\1              using \1 it matches the same text that was matched by the first capturing group -> 
([abc])([de])\2\1      we can use \2 (\3, \4, etc.) to identify the same text that was matched by the second (third, fourth, etc.) capturing group ->
(?<foo>[abc])\k<foo>   we put the name foo to the group and we reference it later (\k<foo>). The result is the same of the first regex ->

### Look-ahead and Look-behind

d(?=r)       matches a d only if is followed by r, but r will not be part of the overall regex match -> 
(?<=r)d      matches a d only if is preceded by an r, but r will not be part of the overall regex match ->
d(?!r)       matches a d only if is not followed by r, but r will not be part of the overall regex match ->
(?<!r)d      matches a d only if is not preceded by an r, but r will not be part of the overall regex match ->

## Author

Written by Shane Sepeda. https://github.com/shane-sepeda
