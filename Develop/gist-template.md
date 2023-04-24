# Understanding REGEX (Regular Expression)

Regular expressions, regex for short. Are strings of special characters that define parameters for a search pattern. They can be utilized in many types of codes and are found accross many coding languages. Although these characters may seem like a random scrible. They are crucial and specifcally placed to define a search pattern. 

## Summary

I will be discussing and analyzing the following expression:


          "^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$"

This regex is used to validate passwords and have the following requirements:

At least one lowercase letter
At least one uppercase letter
At least one digit
At least one special character (@, $, !, %, *, ?, &)
Must be at least 8 characters long
The ^ and $ symbols indicate the start and end of the string, respectively. The (?=.*[a-z]), (?=.*[A-Z]), (?=.*\d), and (?=.*[@$!%*?&]) are positive lookahead assertions that check for the presence of each requirement. Finally, [A-Za-z\d@$!%*?&]{8,} matches any combination of the allowed characters that is at least 8 characters long.


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
The ^ and $ anchors ensure that the entire string matches the pattern, while the . and {8,} specify that the string must be at least 8 characters long. The caret (^): It matches the beginning of the line or string. For example, ^hello will match any string that starts with "hello".

The dollar sign ($) : It matches the end of the line or string. For example, world$ will match any string that ends with "world".

These anchors are often used together to match an entire string from start to finish. For example, ^hello world$ will only match the exact string "hello world" and not any other variations like "hello big world" or "hello worlds".

### Quantifiers

In regular expressions, quantifiers are used to specify how many times a character or group of characters should be matched. Here are some commonly used quantifiers:

*: Matches zero or more occurrences of the preceding character/group.
+: Matches one or more occurrences of the preceding character/group.
?: Matches zero or one occurrence of the preceding character/group.
{n}: Matches exactly n occurrences of the preceding character/group.
{n,}: Matches at least n occurrences of the preceding character/group.
{n,m}: Matches between n and m occurrences of the preceding character/group.

The provided expression is a password validation regex that uses positive lookahead assertions to ensure that the password contains at least one lowercase letter, one uppercase letter, one digit, and one special character from the set @$!%*?&. It then uses a character class [A-Za-z\d@$!%*?&] with a quantifier {8,} to match any combination of these characters that is at least 8 characters long.

### OR Operator

The regex ^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$ uses the OR operator to match a string that meets any of the conditions specified in the lookahead assertions.

The | symbol is used to specify alternatives in a regex pattern. However, in this particular regex, the OR operator is not explicitly used. Instead, it uses positive lookahead assertions to check if the string contains at least one lowercase letter, one uppercase letter, one digit, and one special character from the set @$!%*?&.

Each of these conditions is separated by the AND operator &, which means that all of them must be true for the regex to match. Therefore, the regex matches strings that are at least 8 characters long and contain at least one lowercase letter, one uppercase letter, one digit, and one special character from the set @$!%*?&.

### Character Classes

In the given expression, [a-z] and [A-Z] are character classes. A character class is a set of characters that match any one character from that set. In this case, [a-z] matches any lowercase letter from a to z, and [A-Z] matches any uppercase letter from A to Z.

\d is also a character class, which matches any digit from 0 to 9.

[@$!%*?&] is another character class, which matches any one of the special characters within the brackets.

The expression [A-Za-z\d@$!%*?&] is a combination of multiple character classes, which matches any one character that is either an uppercase or lowercase letter, a digit, or one of the special characters within the brackets.

Overall, character classes are a powerful feature in regex that allow you to match specific sets of characters with ease.

### Flags

Regular expression (regex) flags are optional parameters that modify the behavior of a regex pattern. They are typically denoted by a single letter after the closing delimiter of the regex pattern. Here are some common regex flags:

i: This flag makes the regex pattern case-insensitive, meaning that it will match both uppercase and lowercase letters. For example, the pattern /hello/i would match "hello", "Hello", "hElLo", etc.
g: This flag makes the regex pattern global, meaning that it will match all occurrences of the pattern in the input string, not just the first one. For example, the pattern /o/g would match all the "o" characters in the input string.
m: This flag makes the regex pattern multiline, meaning that it will match the pattern at the beginning of each line, rather than just at the beginning of the entire string. This is useful when dealing with text that contains multiple lines.

### Grouping and Capturing

Regex grouping and capturing are powerful features that allow you to extract specific parts of a match from a regex pattern.

Grouping is the process of enclosing a portion of a regex pattern in parentheses (). This allows you to treat the enclosed portion as a single unit, and apply quantifiers or alternation operators to it. For example, the pattern /(ba)+/ would match any sequence of "ba" characters that appears one or more times, such as "ba", "baba", "bababa", etc. The parentheses around the "ba" sequence indicate that it should be treated as a single unit.

Capturing is the process of extracting the matched groups from a regex pattern. When you use parentheses to create a group, you can refer to the captured text using a backreference. Backreferences are denoted by a backslash followed by the group number, starting from 1. For example, the pattern /(ba)+/ with the input string "baba" would match "baba" and capture "ba" in group 1. You could refer to this captured text using the backreference \1.

In this specific regex pattern, there are four groups that use the (?=) syntax to create positive lookaheads. These groups do not capture any text, but rather assert that certain conditions are met at a particular position in the input string.

For example, (?=.*[a-z]) asserts that there is at least one lowercase letter anywhere in the input string. Similarly, (?=.*\d) asserts that there is at least one digit anywhere in the input string. These groups are used to ensure that the input string meets certain requirements before the final part of the pattern [A-Za-z\d@$!%*?&]{8,} matches the string.

### Bracket Expressions

Regex bracket expressions, also known as character classes, are a way to match a set of characters within a regex pattern.

In this specific pattern, the final part [A-Za-z\d@$!%*?&]{8,} is a bracket expression that matches any character that is either an uppercase or lowercase letter, a digit, or one of the special characters @$!%*?&. The {8,} part at the end indicates that the expression must match at least 8 characters in length.

The square brackets [] denotes a bracket expression. Any character that appears within the brackets is considered a match if it appears in the input string. You can also specify a range of characters using a hyphen -, such as [a-z] to match any lowercase letter from a to z.

In summary, regex bracket expressions allow you to match a set of characters within a regex pattern. In your specific pattern, the bracket expression at the end matches any character that is an uppercase or lowercase letter, a digit, or one of the special characters @$!%*?&, and must be at least 8 characters in length.

### Greedy and Lazy Match

Regex greedy and lazy matching refer to the behavior of quantifiers in a regex pattern. Quantifiers are used to specify how many times a pattern can occur.

Greedy matching is the default behavior of most quantifiers, and it matches as much of the input string as possible. For example, the pattern /a.+/ with the input string "abcde" would match "abcde", because the + quantifier is greedy and matches as many characters as possible after the "a".

Lazy matching, also known as non-greedy or minimal matching, matches as little of the input string as possible. This is useful when you want to match the smallest possible substring that satisfies the pattern. To use lazy matching, you can add a question mark ? after a quantifier. For example, the pattern /a.+?/ with the input string "abcde" would match "ab", because the +? quantifier is lazy and matches as few characters as possible after the "a".

In this specific pattern, there are no quantifiers used, so the question of greedy vs. lazy matching doesn't apply. However, if you were to modify the pattern to include a quantifier, such as /a.+?c/, it would match the smallest possible substring between "a" and "c" using lazy matching.

### Boundaries

Regex boundaries are used to specify the start and end of a word, line, or string in a regex pattern. They are non-capturing assertions that do not match any characters themselves, but rather assert that a certain condition is met at a particular position in the input string.

There are three common regex boundaries:

^: This matches the beginning of a line or string. In your specific pattern, the ^ boundary is used to ensure that the input string begins with the specified pattern.
$: This matches the end of a line or string. In your specific pattern, the $ boundary is used to ensure that the input string ends with the specified pattern.
\b: This matches a word boundary, which is a position between a word character (as defined by \w) and a non-word character. For example, \bcat\b would match the word "cat" but not "caterpillar".
In this specific pattern, the ^ boundary is used to match the beginning of the input string, and the $ boundary is used to match the end of the input string. This ensures that the entire input string matches the pattern, rather than just a portion of it.

### Back-references

Regex back-references are used to refer to previously matched groups in a regex pattern. When you create a capturing group using parentheses (), the text matched by that group is stored in memory and can be referred to later in the pattern using a back-reference.

Back-references are denoted by a backslash followed by the group number, starting from 1. For example, if you have the pattern /(\w)foo\1/ and the input string "afooa", it would match because the \1 back-reference refers to the same character that was matched by the first group, which is "a" in this case.

In this specific pattern, there are no capturing groups used, so back-references are not applicable.

### Look-ahead and Look-behind

Regex look-around assertions, or simply "look-arounds," are non-capturing groups that allow you to check if a pattern matches, without actually including the matched text in the overall match result.

There are two types of look-arounds:

Positive Look-ahead: (?=...): Checks if a pattern exists ahead of the current position, without including it in the match result. If the pattern exists, the match continues from the current position. For example, the pattern /\d(?=\w)/ would match any digit that is immediately followed by a word character.

Negative Look-ahead: (?!...): Checks if a pattern does NOT exist ahead of the current position, without including it in the match result. If the pattern does not exist, the match continues from the current position. For example, the pattern /hello (?!world)/ would match "hello there" but not "hello world".

There are also two types of look-behinds, which work in a similar way to look-aheads:

Positive Look-behind: (?<=...): Checks if a pattern exists behind the current position, without including it in the match result. If the pattern exists, the match continues from the current position. For example, the pattern /(?<=\w)\d/ would match any digit that is immediately preceded by a word character.

Negative Look-behind: (?<!...): Checks if a pattern does NOT exist behind the current position, without including it in the match result. If the pattern does not exist, the match continues from the current position. For example, the pattern /^(?<!not )good/ would match "good" but not "not good".

In this specific pattern, there are four positive look-aheads that are used to check for specific conditions without including them in the overall match result. These look-aheads check if the input string contains at least one lowercase letter, one uppercase letter, one digit, and one special character, respectively.

## Author

I, Sotirios Chortogiannos am a dedicated and enthusiastic full stack engineering student who is passionate about computer programming. With a strong desire to learn and grow in the field, I try my best to keep engaged in expanding my knowledge and developing my skills.

I have a deep respect for everyone and everything around me, and I strive to always do my best in everything I do. The positive attitude and eagerness I try to build and maintain to learn, make me a valuable asset to any team.

Outside of my studies, I enjoy staying active with hobbies like going to the gym, rollerblading, and dancing. I also enjoy being social and meeting new people. With my well-rounded interests and passion for learning, I am sure to make a positive impact wherever I go.