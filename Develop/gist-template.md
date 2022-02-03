# Matching E-mails

This tutorial breaks down the components of a regular expression, also known as regex, to better understand how they work to create useful tools for search patterns.

## Summary

This will briefly summarize and analyze the components that create the expression /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/. This regex is used to match emails, as well as validate inputted emails in Javascript and other popular programming languages.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Metacharacters](#metacharacters)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)


## Regex Components

###  
Anchors belong to a class of characters that specify the position of text. Anchors command either directly adjacent single characters, character classes within [], or groups within ().

* ^ - This anchor represents the beginning of the string.
* $ - This anchor represents the end of the string.

### Quantifiers
Quantifiers are a type of character that dictate the number of specified characters that may be used.

The regex expression contains the `{}` and `+` quanitfiers. 

The `+` quanitifer connects the username + email server + domain (ex. coding `+` @gmail `+` .com).

The `{}` quantifier in the expression matches when the preceding character, or character group occurs n times. In the expression in our example, `{2,6}` will allow a match range of 2-6 characters for the character set `[a-z\.]`. Example, `username@gmail.abc` will be allowed, but `username@gmail.abcdefgh` will not be a match as it exceeds 6 characters.

### Metacharacters
Metacharacters, as opposed to literal characters, are characters imbued with special meaning. The `\` is a very common example, used in combinations such as `\d` as shorthand for the [character class](#character-classes) `[0-9]` for any digit, `\w` for any alphanumeric, `\s` for any whitespace, and so on. In our example, `\d` is used in group 2 to specify any digit, 0-9, as seen in the following snippet: `([\da-z.-]+)`. It should be noted that when placed inside a [character class](#character-classes) `[]`, metacharacters other than `\`, `^` (anything NOT, if first--otherwise literal) or `-` (literal if first, otherwise means "through," as in 0-9) are processed as literal characters, and thus lose their special meaning when placed within them. See [Bracket Expressions](#bracket-expressions) for more information.

Examples from the regex email expression: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

`\`: `([\da-z\.-]+)` A metacharacter `\` combines with `d` to denote [character class](#character-classes) `[0-9]`. Notice this is effectively an example of a [character class](#character-classes) nested inside another [character class](#character-classes).

### Character Classes
The metacharacter `/d` is used to match a single digit. This is searched in the email server portion of the email address.

The metacharacter `[]` is used to match any single character present in the set. There are 3 character sets that can be identified in the entire regex expression:

* `[a-z0-9_\.-]` translates to a matching character set that contains any character from the range between a-z (case-sensitive) (case-sensitive), any digit from the range between 0-9, including underscores (_), a period (\.), or hyphen (-). This is defined as the first character set for the username portion of the email address.

* `[\da-z\.-]` translates to a matching character set that contains any digit form 0-9, any character from the range between a-z (case-sensitive), a period (\.), or hyphen (-). This is defined as the second character set for the email server portion of the email address.

* `[a-z\.]` translates to a matching characyer set that contains any character from the range between a-z (case-sensitive) and a period (\.). This is defined as the third character set for the domain portion of the email address.

### Grouping and Capturing
There are 3 groups using the parentheses`()` in this express.
* `([a-z0-9_\.-]+)` is the 1st capturing group for the username
* `([\da-z\.-]+)` is the 2nd capturing group for the email server
* `([a-z\.]{2,6})` is rhe 3rd capturing grop for the domain

### Bracket Expressions
The metacharacter `[]` is used to match any single character present in the set. There are 3 character sets that can be identified in the entire regex expression:

* `[a-z0-9_\.-]` translates to a matching character set that contains any character from the range between a-z (case-sensitive), any digit from the range between 0-9, including underscores (_), a period (\.), or hyphen (-). This is defined as the first character set for the username portion of the email address.

* `[\da-z\.-]` translates to a matching character set that contains any digit form 0-9, any character from the range between a-z (case-sensitive), a period (\.), or hyphen (-). This is defined as the second character set for the email server portion of the email address.

* `[a-z\.]` translates to a matching characyer set that contains any character from the range between a-z (case-sensitive) and a period (\.). This is defined as the third character set for the domain portion of the email address.

### Greedy and Lazy Match
The `+` quantifier matches the preceding character set as many times as posisble, giving back as needed. The `{}` qunaitifer also matches when the preceding character, or character group occurs n times. In our expression, `{2,6}` matches the preceding character set `[a-z\.]` 2-6 times, as many times as possible, giving back as needed.

## Author
Visit my Github and take a peak at my projects: https://github.com/bryance97

I am currently enrolled in the Rutgers Bootcamp for Web Development