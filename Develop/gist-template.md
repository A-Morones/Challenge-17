# Adalberto's Regex Tutorial

In this Regex Tutorial I will explain how a specific regular expression, or regex functions by breaking down each part of the expression and describing what it does.

## Summary

You will learn how to validate the featured email address regular expression (regex) Regex Featured in This Tutorial: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors
In regular expressions (regex), anchors are special characters that define the position of the match within a string. They do not match any characters themselves but rather specify the location where a match should occur. Anchors are useful for specifying where a pattern should start or end.

Common Anchors: 
1. ^ (Caret): Matches the position at the start of a string. Useful for ensuring that a pattern occurs at the start of the string.
2. $ (Dollar Sign): Matches the position at the end of a string. Useful for ensuring that a pattern occurs at the end of the string.

### Quantifiers
In regular expressions (regex), quantifiers specify how many times a particular element (character, group, or pattern) can occur. They control the number of repetitions of a pattern and are crucial for matching patterns that appear a specific number of times or within a range.

+: + indicates that the previous character must occur at least one or more times.
?: ? indicates that the preceding character is optional. It means the preceding character can occur zero or one time.
*: Matches zero or more of the preceding character.
{n}: Matches exactly n occurrences of the preceding character.
{n,}: Matches n or more occurrences of the preceding character.
{n,m}: Matches between n and m occurrences of the preceding element

### Grouping Constructs
Grouping constructs delineate the subexpressions of a regular expression and capture the substrings of an input string. You can use grouping constructs to do the following:

1. Match a subexpression that's repeated in the input string.
2. Apply a quantifier to a subexpression that has multiple regular expression language elements.
3. Include a subexpression in the string that's returned by the xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType and xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType methods.
4. Retrieve individual subexpressions from the xref:System.Text.RegularExpressions.Match.Groups?displayProperty=nameWithType property and process them separately from the matched text as a whole.

### Bracket Expressions
A bracket expression is either a matching list expression or a non-matching list expression. It consists of one or more expressions: ordinary characters, collating elements, collating symbols, equivalence classes, character classes, or range expressions. The <right-square-bracket> ( ']' ) shall lose its special meaning and represent itself in a bracket expression if it occurs first in the list (after an initial <circumflex> ( '^' ), if any). Otherwise, it shall terminate the bracket expression, unless it appears in a collating symbol (such as "[.].]" ) or is the ending <right-square-bracket> for a collating symbol, equivalence class, or character class. The special characters '.', '*', '[', and '\\' ( <period>, <asterisk>, <left-square-bracket>, and <backslash>, respectively) shall lose their special meaning within a bracket expression.

The character sequences "[.", "[=", and "[:" ( <left-square-bracket> followed by a <period>, <equals-sign>, or <colon>) shall be special inside a bracket expression and are used to delimit collating symbols, equivalence class expressions, and character class expressions. These symbols shall be followed by a valid expression and the matching terminating sequence ".]", "=]", or ":]", as described in the following items.

### Character Classes
In regular expressions (regex), character classes are a fundamental feature that allows you to define a set of characters to match. They enable you to specify a range of acceptable characters in a position within a string.

1. Character class: Matches any one of the enclosed characters. You can specify a range of characters by using a hyphen, but if the hyphen appears as the first or last character enclosed in the square brackets, it is taken as a literal hyphen to be included in the character class as a normal character.

For example, [abcd] is the same as [a-d].

2. Negated character class: Matches anything that is not enclosed in the square brackets. You can specify a range of characters by using a hyphen, but if the hyphen appears as the first character after the ^ or the last character enclosed in the square brackets, it is taken as a literal hyphen to be included in the character class as a normal character. 

For example, [^abc] is the same as [^a-c].

### The OR Operator
In regular expressions (regex), the "or" operator is used to specify alternatives within a pattern. This allows you to match one of several possible patterns. The operator is represented by the pipe symbol (|).

1. Simple Alternation
Description: Matches either of the patterns separated by |.

2. Grouping with Alternation
Description: You can group patterns using parentheses to apply alternation within a specific part of the regex.
Example: (cat|dog)s matches "cats" or "dogs".

3. Combining Alternation with Quantifiers
Description: You can use the "or" operator with quantifiers to match a range of different patterns.
Example: colou?r matches both "color" and "colour" because u? means "u" is optional.

4. Nested Alternation
Description: You can use alternation within nested groups to create more complex patterns.
Example: (a|b|c)(x|y|z) matches "ax", "ay", "az", "bx", "by", "bz", "cx", "cy", or "cz".

5. Alternation with Non-Capturing Groups
Description: You can use non-capturing groups with alternation to avoid capturing groups that you do not need.
Example: (?:cat|dog)s matches "cats" or "dogs" without capturing the group.

### Flags
A flag is an optional parameter to a regex that modifies its behavior of searching. A flag changes the default searching behavior of a regular expression. It makes a regex search in a different way. A flag is denoted using a single lowercase alphabetic character.

Examples: 
Flag:i	

Name: Ignore Casing

Modification: Makes the expression search case-insensitively.

Flag: g

Name: Global

Modification: Makes the expression search for all occurrences.

Flag: s	

Name: Dot All

Modification: Makes the wild character . match newlines as well.

Flag: m	

Name: Multiline		

Modification: Makes the boundary characters ^ and $ match the beginning and ending of every single line instead of the beginning and ending of the whole string.

Flag: y	

Name: Sticky

Modifiction: Makes the expression start its searching from the index indicated in its lastIndex property.

Flag: u	

Name: Unicode			

Modification: Makes the expression assume individual characters as code points, not code units, and thus match 32-bit characters as well.

### Character Escapes
In regular expressions (regex), character escapes allow you to match special characters or sequences that otherwise have a different meaning in regex syntax. Escaping is essential when you need to include literal characters in your pattern or use special sequences for specific purposes.

1. Literal Characters

Description: To include characters that have special meanings in regex, such as . or *, you need to escape them with a backslash (\).

Example: \. matches a literal dot character rather than any character.

2. Escaping Special Characters

Description: Special characters like \, ., +, ?, *, |, (), {}, [], ^, $, and - need to be escaped with a backslash to be treated as literal characters.

Example: \* matches a literal asterisk *.

\\: Escapes a backslash.
\.: Matches a literal dot.
\d: Matches a digit.
\D: Matches a non-digit.
\w: Matches a word character.
\W: Matches a non-word character.
\s: Matches a whitespace character.
\S: Matches a non-whitespace character.
\b: Matches a word boundary.
\B: Matches a non-word boundary.
\n, \r, \t, etc.: Matches specific whitespace characters.
\x and \u: Matches characters using hexadecimal or Unicode escapes.

Character escapes are crucial for accurately matching and processing text using regex patterns. They help you specify exact characters or sequences and manage the special meanings of characters within patterns.

## Author

Adalberto Morones
Github Link: https://github.com/A-Morones
Github Repository: https://github.com/A-Morones/Challenge-17
