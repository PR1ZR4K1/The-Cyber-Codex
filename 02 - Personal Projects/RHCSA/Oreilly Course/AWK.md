2024/04/09 10:03
Status: #idea
Tags: [[Linux]], [[Linux - Basic Commands]], [[Manage Files from the CLI]], [[Command line Interface]]

### AWK Command Overview

`awk` is a versatile programming language and command-line tool used for pattern scanning and processing. It's particularly powerful for processing and analyzing text files, especially for data extraction, reporting, and transformation tasks.

### Basic Syntax

The basic syntax of the `awk` command is:

arduinoCopy code

`awk [options] 'program' file`

- `options`: Command line options to modify `awk`'s behavior.
- `program`: A set of instructions for `awk` to execute, often enclosed in single quotes.
- `file`: The input file(s) on which `awk` operates.

### Common Options

- `-f file`: Reads the `awk` program from a file.
- `-F fs`: Sets the input field separator to `fs`.

### Core Concepts

- **Pattern matching**: `awk` processes each line of a file looking for patterns that match the specified criteria and performs the specified action on matching lines.
- **Fields and Records**: By default, `awk` treats each line as a record and spaces and tabs as field separators, making `$1`, `$2`, etc., represent each word or field in a line.
- **Built-in Variables**: `awk` has built-in variables like `FS` (field separator), `OFS` (output field separator), `NR` (number of records), and `NF` (number of fields).

### Common Use Cases and Examples

#### 1. Printing Columns

Print the first column of a file:

arduinoCopy code

`awk '{print $1}' filename`

#### 2. Summing Up a Column's Values

Sum the values of the first column:

arduinoCopy code

`awk '{sum += $1} END {print sum}' filename`

#### 3. Filtering Based on Column Value

Print lines where the value of the second column is greater than 10:

arduinoCopy code

`awk '$2 > 10' filename`

#### 4. Transforming Data

Add a new column showing the sum of the first and second columns:

swiftCopy code

`awk '{print $1, $2, $1 + $2}' filename`

#### 5. Text Processing with Patterns

Print lines that match a specific pattern (e.g., lines containing "pattern"):

arduinoCopy code

`awk '/pattern/' filename`







---
# References
