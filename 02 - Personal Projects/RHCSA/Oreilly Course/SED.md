2024/04/09 09:53
Status: #idea
Tags: [[Command line Interface]], [[Linux]], [[Linux - Basic Commands]]

# Stream Editor

sed ("stream editor") is a Unix utility that parses and transforms text, using a simple, compact programming language. It was developed from 1973 to 1974 by Lee E. McMahon of Bell Labs, and is available today for most operating systems.

### sed Command Syntax

The basic syntax for `sed` (Stream Editor) in the Unix/Linux command line is:

arduinoCopy code

`sed [options] 'command' file`

- `options` are used to alter the default behavior of `sed`.
- `command` is the action to perform on the input data.
- `file` is the source of input data (a file on your filesystem).

### Common Options

- `-i`: Edit files in-place (makes changes to the original file).
- `-e`: Allows the execution of multiple `sed` commands in a single run.
- `-n`: Suppresses automatic printing of the pattern space, making `sed` only produce output when explicitly told to via the `p` command.

### Common Commands

- `s/pattern/replacement/`: Substitutes the `pattern` with the `replacement` string.
- `p`: Prints the pattern space (usually used with `-n`).
- `d`: Deletes the pattern space (removes the line).

### Use Cases and Examples

#### 1. Text Substitution

Replace the first occurrence of "text" with "word" in a file:

arduinoCopy code

`sed 's/text/word/' filename`

Replace all occurrences of "text" with "word" in a file:

arduinoCopy code

`sed 's/text/word/g' filename`

#### 2. In-Place File Editing

To make changes directly in the file (edit in-place):

arduinoCopy code

`sed -i 's/text/word/g' filename`

#### 3. Delete Lines

Delete lines matching a specific pattern:

arduinoCopy code

`sed '/pattern_to_match/d' filename`

Delete a specific line (e.g., the 2nd line):

arduinoCopy code

`sed '2d' filename`

#### 4. Print Specific Lines

Print only lines matching a specific pattern:

arduinoCopy code

`sed -n '/pattern_to_match/p' filename`

#### 5. Multiple Commands

Execute multiple `sed` commands on a file:

arduinoCopy code

`sed -e 's/text/word/' -e '/^$/d' filename`

This replaces "text" with "word" and deletes empty lines.

### Conclusion

`sed` is a powerful stream editor for filtering and transforming text in files or input from a pipeline. Its versatility makes it a valuable tool for scripting and data manipulation tasks. Remember that `sed` works line by line and supports regular expressions, which makes it incredibly powerful for pattern matching and text processing.





---
# References
