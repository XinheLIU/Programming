# Basic

* c - matches character c, unless c is regular expression
* ^ - start of string
* $ - end of string
* . - matches any char
* \[abc\] - either a or b or c
* \[^abc\] - matches one character, not a or b or c
* \[a-z\] - matches one char, in range a through z
* c\* - matches a sequence of 0 or more occurance
* \c - matches c, even if c is regular expression
* use py raw string feature r'&lt;str&gt;'

# Operations

* e1 \| e2 - match e1 or e2
* \(e\) - creates a group
  * \n - matches the n th group
* e+ - matches a sequence of 1 or more e
* e? mathes 0 or 1 e

Combine

```
pat = r'(...).*\1' # contains some 3-char sequence at least twice
pat = r '(.)(.)(.) .*\3\1\2' # contains a 3-char seq, followed by same chars in different order
```



