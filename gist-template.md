# Regular "Reg(gie)Ex" Expressions

This is my take on regex, a purposeful tool that confuses most who know a thing a bout it. Hopefully, my view can demystify the string of characters that gives the user a tool to create patterns to match, locate and manage text.

## Summary

This is a brief summary of the search pattern used in a body of text. I will be evaluating the regualar expression for Matching a URL.

```
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/
```

With an interest in server side coding this seems like a useful tool that I will need to use more than once as in my lifetime. Regular expressions are useful because they provide more flexible and powerful pattern matching than you can achieve with wildcards.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Back-references](#back-references)
- [Resources](#resources)

## Regex Components

### Anchors

Also known as "atomic zero-width assertions", these special characters specify a position in the string where a match must occur. The regular expression engine looks for a match in the specified position only. The caret at the start of this expression is one example of an anchor.

```
([\/\w \.-]*)*\/?$/
```

The "$" towards the end of the expression signifies the matches must happen at the end of a string or line. Another possibility is to use the "\n" flag woule indicate a new line being formed/evaluated.

### Quantifiers

The following quantifiers want to match as many characters as possible):

- ?: match never or once
- \*: match zero or more times
- +: match one or more times
- {n}: match n times
- {n,}: match n or more times
- {n,m}: match at least n times, at most m times.

To find a match with as few characters as possible, you will have to put question marks (?) after these characters.

```
(https?:\/\/)?
```

The first use of a quantifier in the Matching a URL expression we are evaluating is found after the "https". The "?" will ensure the correct protocol is used for the URL string. Seeing how the preceeding five characters are not escaped the group of characters will be matched as is to form the hypertext protocol for secure browser communitcation.

### OR Operator

You can the "|" (OR operator) to provide as many terms as desired, as long as they are separated with the Vertical bar character. This character separates terms contained within each group. The expression we are evaluating for matching a URL does not contain a vertical bar.

### Character Classes

- Caret ^ - The first character of the string used to compose the regular expression is the same unless you are beginning a multline statement. At which case you will enable the multiline flag (m).

- Square brackets[ ] - represents exactly one character

  - [abc] a or b or c
  - [^abc] any character _except_ a, b, or c, (negation)
  - [a-zA-Z] a through z or A through Z, (range)

- Back Slash \ - The following characters need to be preceded by a backslash if they are to be used without special meaning:
  \ . $ \* ? + [ ] ( ) | { }

- Vertical Bar | - is common to JavaScript as the OR operator and is identified the same in regex.

Parenthesis ( ) - Used to group expressions.

A Single Character - Match any string of characters to create an expression. Ranges of characters are specified via dashes: [a-z]

### Flags

There are a few characters that can be used as flags when added to the end of an expression. They are "g (global) which matches multiple times, i (ignoreCase) is case-insensative, m(multiline), s(dotAll), u(unicode, y(sticky))"

### Grouping and Capturing

Parentheses help show the text matched by the regex inside them. This allows you to apply regex operators to the entire grouped regex.

In the Matching a URL expression, there are four capturing groups.

```
1)  (https?:\/\/)
```

```
2)  ([\da-z\.-]+)
```

```
3)  ([a-z\.]{2,6})
```

```
4)  ([\/\w \.-]*)
```

The third capturing group ([a-z\.]{2,6}) shows a single matching character from the range a-z and is case sensitive. In the square brackets holding this range is the "\.", which is also case sensitive and matches the "." needed to formulate a URL. This is matched between 2 and 6 times and is considered greedy.

### Bracket Expressions

The square brackets create a list of possible matches. Inside the square brackets of the Matching a URL example, the fourth capuring group had the following:

```
([\/\w \.-]*)
```

This can be broken down to a separator forward slash that is escaped, meaning the match will appear as it does in the expression. This is followed by the "\w" indicating any word will match this part of the expression. Followed by a space, the an escaped period. The hyphen that follows will be strictly matched as well. The wild card character prior to the closing parenthesis signifies this portion of the expressiong will be matched as many times as necessary to find all of the matches and is considered greedy.

### Greedy and Lazy Match

The term greedy seems funny to include evaluating an expression however, when defined it fits as an apt explanation. The RegEx engine used to evaluate the strings will search every position in the string to find a match. If there are no matches at the current position, it will continue onto the next available position.

The wildcard used at the end of this capturing group is considered greedy because it will search for matches between zero and an unlimited amount of times.

```
([\/\w \.-]*)
```

A lazy mode of qualifiers is used by the "?". When the question mark is used after another qualifier it instructs that search to happen the least amount of times possible. In the Matching a URL expression,

```
(https?:\/\/)
```

the "?" is requiring the search for https only happen once. This makes since, as that combination would not be repeated in a valid URL.

### Back-references

The way you can check each group of parentheses to determin what is captured by the text matched by the regex inside them into a numbered group that can be reused with a numbered backreference. In some instances the backreferebces are named to make searching for them easier.

## Resources

#### RegExr

RegExr is an online tool to learn, build, & test Regular Expressions (RegEx / RegExp).
https://regexr.com/

#### Loyola Marymount University - Computer Science

https://cs.lmu.edu/~ray/notes/regex/

#### Wiki - Regular Language

https://en.wikipedia.org/wiki/Regular_language

#### Exploring JavaScript

https://exploringjs.com/impatient-js/ch_regexps.html

#### ocpsoft

https://www.ocpsoft.org/tutorials/regular-expressions/or-in-regex/

## Author

Donald Bull is a Web Developer from Austin. Who started buiding websites for friends and family early on using Google sites then more user friendly options like Wix and WordPress. The opportunity came to make a go of it full time and not looking back the determined coder searches for more ways to hone his craft.
