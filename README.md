# Text Processing Lecture Example Files

Quick reference of common regex along with their descriptions and examples.

---

### **Common Regular Expressions (Regex) Table**

| **Regex Pattern** | **Description**                            | **Example** | **Matches**                                      |
|-------------------|--------------------------------------------|-------------|--------------------------------------------------|
| `.`               | Matches **any single character**           | `a.b`       | Matches `aab`, `acb`, `a1b`                      |
| `^`               | **Anchors** the match to the **start** of a line | `^Hello`    | Matches lines starting with "Hello"              |
| `$`               | **Anchors** the match to the **end** of a line   | `world$`    | Matches lines ending with "world"                |
| `*`               | Matches **zero or more** of the preceding character | `a*`        | Matches `a`, `aa`, or an empty string            |
| `+`               | Matches **one or more** of the preceding character | `a+`        | Matches `a`, `aa`, but not an empty string       |
| `?`               | Matches **zero or one** of the preceding character | `a?`        | Matches `a` or an empty string                   |
| `\d`              | Matches any **digit** (equivalent to `[0-9]`) | `\d{3}`     | Matches any three-digit sequence (e.g., `123`)   |
| `\D`              | Matches any **non-digit** character         | `\D+`       | Matches `abc`, `xyz`, or any non-numeric string  |
| `\w`              | Matches any **word character** (alphanumeric or underscore) | `\w+`   | Matches `word1`, `abc_123`, `A_B`                |
| `\W`              | Matches any **non-word character**          | `\W+`       | Matches spaces, punctuation, etc. (e.g., `!`, `@`) |
| `\s`              | Matches any **whitespace** character        | `\s+`       | Matches spaces, tabs, newlines                   |
| `\S`              | Matches any **non-whitespace** character    | `\S+`       | Matches `text`, `abc123`                         |
| `[abc]`           | Matches any **one character** in the set    | `[aeiou]`   | Matches any vowel (e.g., `a`, `e`, `i`, etc.)    |
| `[^abc]`          | Matches any **character not** in the set    | `[^aeiou]`  | Matches any non-vowel character                  |
| `(a|b)`           | **Alternation**, matches either `a` or `b`  | `(cat|dog)` | Matches `cat` or `dog`                           |
| `{n}`             | Matches **exactly n** occurrences           | `\d{3}`     | Matches exactly three digits (e.g., `123`)       |
| `{n,}`            | Matches **n or more** occurrences           | `\d{3,}`    | Matches three or more digits                     |
| `{n,m}`           | Matches **between n and m** occurrences     | `\d{2,4}`   | Matches between two and four digits              |
| `(?i)`            | **Case-insensitive** matching               | `(?i)hello` | Matches `hello`, `Hello`, `HELLO`                |
| `\b`              | **Word boundary**                           | `\bword\b`  | Matches the exact word "word"                    |
| `\B`              | **Non-word boundary**                       | `\Bword\B`  | Matches "word" as part of a larger string (e.g., `password`) |
| `\.`              | Escapes special character `.` to match a literal dot | `\.`   | Matches `.` (dot) literally                      |
| `(?=...)`         | **Positive lookahead** (matches if ... follows) | `foo(?=bar)`| Matches `foo` only if it's followed by `bar`     |
| `(?!...)`         | **Negative lookahead** (matches if ... does not follow) | `foo(?!bar)` | Matches `foo` only if it's **not** followed by `bar` |
| `(?<=...)`        | **Positive lookbehind** (matches if ... precedes) | `(?<=@)\w+` | Matches word after `@` in `email@example.com`    |
| `(?<!...)`        | **Negative lookbehind** (matches if ... does not precede) | `(?<!@)\w+` | Matches word not preceded by `@`                |

---

### **Regex Examples**

1. **Matching an Email Address**:
   ```regex
   [a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}
   ```
   - Matches an email address (e.g., `name@example.com`).

2. **Matching a Phone Number** (e.g., `(123) 456-7890`):
   ```regex
   \(\d{3}\)\s\d{3}-\d{4}
   ```

3. **Extracting a Year from a Date** (e.g., `2023-10-16`):
   ```regex
   \d{4}
   ```
   - Matches a 4-digit year.

4. **Matching Only Whole Words**:
   ```regex
   \bcat\b
   ```
   - Matches the word "cat", but not "catch" or "concatenate".

5. **Finding Duplicate Words**:
   ```regex
   \b(\w+)\s+\1\b
   ```
   - Matches repeated words (e.g., "hello hello").

6. **Matching an IPv4 Address**:
   ```regex
   \b\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}\b
   ```
   - Matches an IP address like `192.168.0.1`.

---

### **Useful Regex in Linux (`grep`/`sed`)**

1. **Find lines that start with a digit**:
   ```bash
   grep '^[0-9]' file.txt
   ```

2. **Find lines that end with a period**:
   ```bash
   grep '\.$' file.txt
   ```

3. **Replace a word only if it appears as a whole word**:
   ```bash
   sed 's/\bfoo\b/bar/g' file.txt
   ```

4. **Extract email addresses from a file**:
   ```bash
   grep -Eo '[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}' file.txt
   ```
