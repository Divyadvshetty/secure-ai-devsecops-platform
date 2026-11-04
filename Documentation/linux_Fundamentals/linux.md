# Day 5 — Linux Text Processing and File Searching

Day 5
2 hours
Beginner to intermediate

Today's objective: Learn how to search for files, filter log entries, extract information from text, sort records, remove duplicates and process large files using Linux commands.

This is one of the most important practical Linux lessons for DevOps engineers. In production, engineers rarely read every line of a log file manually. They use commands to extract the information needed to diagnose a problem.

Connection to previous days:

- Day 1: Operating systems and Linux architecture.
- Day 2: Linux boot process and system initialisation.
- Day 3: Filesystem hierarchy and navigation.
- Day 4: File creation, inspection, copying and management.
- Day 5: Searching and processing file contents efficiently.

By the end of this class, students should be able to investigate application logs, locate configuration files, extract failed transactions and perform basic text analysis directly from the Linux terminal.

## 1. Today's timetable

| Time         | Duration | Topic                                |
| ------------ | -------- | ------------------------------------ |
| 00:00–00:10 | 10 min   | Recap and introduction               |
| 00:10–00:25 | 15 min   | Finding files with find              |
| 00:25–00:45 | 20 min   | Searching text using grep            |
| 00:45–01:00 | 15 min   | Extracting data using cut            |
| 01:00–01:15 | 15 min   | Sorting and removing duplicates      |
| 01:15–01:30 | 15 min   | Text transformation using tr and sed |
| 01:30–01:45 | 15 min   | Introduction to awk                  |
| 01:45–01:55 | 10 min   | Production troubleshooting exercise  |
| 01:55–02:00 | 5 min    | Revision and homework                |

## Part 1 — Why do DevOps engineers need text processing?

00:00–00:10 · 10 minutes

### 1.1 Start with a production example

Imagine an application running on a Linux server.

Its application log contains 100,000 lines.

Example:

```text
2026-11-04 10:00:01 INFO Application started
2026-11-04 10:00:05 INFO Database connected
2026-11-04 10:00:10 INFO User login successful
2026-11-04 10:01:12 ERROR Database connection timeout
2026-11-04 10:01:15 INFO Retry initiated
2026-11-04 10:01:30 ERROR Database connection failed
2026-11-04 10:02:00 INFO Health check successful
```

Ask students:

1. How do you find only ERROR messages?
2. How do you count the number of errors?
3. How do you extract only timestamps?
4. How do you identify unique error messages?
5. How do you sort records?
6. How do you search for a particular user ID?

Reading the entire file manually is inefficient.

Linux provides commands to perform these operations.

### 1.2 Today's command toolkit

| Command | Purpose                                     |
| ------- | ------------------------------------------- |
| find    | Find files and directories                  |
| grep    | Search text                                 |
| cut     | Extract fields or character positions       |
| sort    | Sort lines                                  |
| uniq    | Identify or remove adjacent duplicate lines |
| wc      | Count lines, words and bytes                |
| tr      | Translate or delete characters              |
| sed     | Stream-based text editing                   |
| awk     | Process structured text and fields          |
| xargs   | Build command arguments from input          |

Explain that these tools are frequently combined using pipes.

We will first understand each command independently and then combine them.

## Part 2 — Finding files using find

00:10–00:25 · 15 minutes

### 2.1 What is find?

`find` searches for files and directories within a specified starting location.

Syntax:

```bash
find PATH EXPRESSION
```

For example:

```bash
find /etc -name "hosts"
```

This searches under `/etc` for entries named `hosts`.

Explain:

- `/etc` is the starting directory.
- `-name` is the search condition.
- `"hosts"` is the filename pattern.

Unlike `locate`, which generally uses a database, `find` searches the directory tree itself.

### 2.2 Prepare a training directory

Ask students to create this structure:

```bash
mkdir -p ~/linux-training/day5/{logs,config,scripts,backup}
```

Create sample files:

```bash
touch ~/linux-training/day5/logs/app.log
touch ~/linux-training/day5/logs/error.log
touch ~/linux-training/day5/logs/access.log

touch ~/linux-training/day5/config/app.conf
touch ~/linux-training/day5/config/database.conf

touch ~/linux-training/day5/scripts/start.sh
touch ~/linux-training/day5/scripts/stop.sh

touch ~/linux-training/day5/backup/old-app.log
```

### 2.3 Find files by name

Find all files named `app.log`:

```bash
find ~/linux-training/day5 -name "app.log"
```

Find all `.log` files:

```bash
find ~/linux-training/day5 -name "*.log"
```

Find all `.conf` files:

```bash
find ~/linux-training/day5 -name "*.conf"
```

Explain the wildcard:

- `*` represents zero or more characters.
- `*.log` means any filename ending in `.log`.

Case-insensitive filename search:

```bash
find ~/linux-training/day5 -iname "*.LOG"
```

`-iname` ignores case when matching the filename.

### 2.4 Find only files or directories

Find regular files:

```bash
find ~/linux-training/day5 -type f
```

Find directories:

```bash
find ~/linux-training/day5 -type d
```

Important types:

| Type | Meaning       |
| ---- | ------------- |
| f    | Regular file  |
| d    | Directory     |
| l    | Symbolic link |

Find symbolic links:

```bash
find ~/linux-training/day5 -type l
```

### 2.5 Find files based on size

Find files larger than 1 MB:

```bash
find ~/linux-training/day5 -type f -size +1M
```

Find files smaller than 1 MB:

```bash
find ~/linux-training/day5 -type f -size -1M
```

Explain:

- `+` means greater than the specified size.
- `-` means less than the specified size.

Find zero-byte files:

```bash
find ~/linux-training/day5 -type f -empty
```

### 2.6 Find files based on modification time

This is especially useful in production.

Find files modified within the last day:

```bash
find ~/linux-training/day5 -type f -mtime -1
```

Find files modified more than seven days ago:

```bash
find ~/linux-training/day5 -type f -mtime +7
```

Find files modified in the last 60 minutes:

```bash
find ~/linux-training/day5 -type f -mmin -60
```

Explain:

- `mtime` measures modification age in 24-hour periods.
- `mmin` measures modification age in minutes.
- `-mtime -1` does not mean exactly 24 hours of precision; for minute-level investigation use `-mmin`.

### 2.7 Production scenario — locate large log files

Problem: A Linux server is running out of disk space.

The engineer wants to identify large log files.

```bash
find /var/log -type f -size +100M -ls
```

Explain:

- Search starts at `/var/log`.
- Only regular files are considered.
- Files larger than 100 MB are selected.
- `-ls` displays detailed information about matching entries.

Another useful command:

```bash
find /var/log -type f -name "*.log"
```

Trainer warning: Searching system directories may produce permission errors. Do not immediately run every search using `sudo`. First understand the search scope and whether elevated privileges are actually needed.

## Part 3 — Searching text using grep

00:25–00:45 · 20 minutes

### 3.1 What is grep?

`grep` searches text for a pattern and displays matching lines.

Syntax:

```bash
grep [OPTIONS] PATTERN FILE
```

Think of a log file containing thousands of entries. Instead of reading every line, `grep` extracts the lines matching the condition.

### 3.2 Prepare a sample application log

Create a log file:

```bash
cat > ~/linux-training/day5/logs/app.log <<'EOF'
2026-11-04 10:00:01 INFO user=101 action=login status=success
2026-11-04 10:00:05 INFO user=102 action=login status=success
2026-11-04 10:01:12 ERROR user=103 action=payment status=failed
2026-11-04 10:01:15 WARN user=104 action=login status=retry
2026-11-04 10:01:30 ERROR user=105 action=payment status=failed
2026-11-04 10:02:00 INFO user=106 action=logout status=success
2026-11-04 10:02:30 ERROR user=107 action=database status=timeout
2026-11-04 10:03:00 INFO user=108 action=login status=success
2026-11-04 10:04:00 WARN user=109 action=payment status=pending
2026-11-04 10:05:00 ERROR user=110 action=database status=timeout
EOF
```

Display the file:

```bash
cat ~/linux-training/day5/logs/app.log
```

### 3.3 Search for ERROR messages

```bash
grep "ERROR" ~/linux-training/day5/logs/app.log
```

Expected output:

```text
2026-11-04 10:01:12 ERROR user=103 action=payment status=failed
2026-11-04 10:01:30 ERROR user=105 action=payment status=failed
2026-11-04 10:02:30 ERROR user=107 action=database status=timeout
2026-11-04 10:05:00 ERROR user=110 action=database status=timeout
```

Explain: Only lines containing the requested pattern are displayed.

### 3.4 Important grep options

| Option | Purpose                              |
| ------ | ------------------------------------ |
| -i     | Ignore case                          |
| -n     | Display matching line numbers        |
| -v     | Display non-matching lines           |
| -c     | Count matching lines                 |
| -r     | Search recursively                   |
| -l     | Display filenames containing matches |
| -w     | Match whole words                    |
| -E     | Use extended regular expressions     |

Demonstrate each.

Case-insensitive search:

```bash
grep -i "error" ~/linux-training/day5/logs/app.log
```

Show line numbers:

```bash
grep -n "ERROR" ~/linux-training/day5/logs/app.log
```

Count matching lines:

```bash
grep -c "ERROR" ~/linux-training/day5/logs/app.log
```

Expected output:

```text
4
```

Show lines that do not contain ERROR:

```bash
grep -v "ERROR" ~/linux-training/day5/logs/app.log
```

Search recursively through directories:

```bash
grep -r "ERROR" ~/linux-training/day5/logs
```

Display only filenames containing ERROR:

```bash
grep -rl "ERROR" ~/linux-training/day5
```

### 3.5 Searching for multiple patterns

Find either ERROR or WARN:

```bash
grep -E "ERROR|WARN" ~/linux-training/day5/logs/app.log
```

Explain:

- `-E` enables extended regular expression syntax.
- `|` means OR in this expression.

Find lines beginning with ERROR:

```bash
grep "^ERROR" somefile.log
```

But our training log starts with a timestamp. Therefore:

```bash
grep " ERROR " ~/linux-training/day5/logs/app.log
```

Find lines ending in timeout:

```bash
grep "timeout$" ~/linux-training/day5/logs/app.log
```

Explain:

- `^` means the beginning of a line.
- `$` means the end of a line.

### 3.6 Production scenario — investigate failed transactions

Suppose the application team reports payment failures.

Search:

```bash
grep "action=payment" ~/linux-training/day5/logs/app.log
```

Search only failed payments:

```bash
grep "action=payment" ~/linux-training/day5/logs/app.log | grep "status=failed"
```

Count failed payments:

```bash
grep "action=payment" ~/linux-training/day5/logs/app.log | grep -c "status=failed"
```

Expected output:

```text
2
```

This introduces an important Linux concept: pipes.

## Part 4 — Understanding pipes and command chaining

00:45–00:50 · 5 minutes (included in the grep section)

A pipe (`|`) sends the standard output of one command to the standard input of another command.

Example:

```bash
grep "ERROR" app.log | wc -l
```

How does this work?

1. `grep "ERROR" app.log` finds matching lines.
2. The pipe sends those lines to the next command.
3. `wc -l` counts the lines it receives.
4. The final output is the number of ERROR entries.

Another example:

```bash
cat app.log | grep "ERROR"
```

This works, but is generally unnecessary. Prefer:

```bash
grep "ERROR" app.log
```

Explain that `cat` is not required when `grep` can read the file directly.

Important distinction:

- `>` redirects output to a file.
- `>>` appends output to a file.
- `|` sends output to another command.

Example:

```bash
grep "ERROR" app.log > errors.txt
```

This saves matching lines to `errors.txt`.

## Part 5 — Extracting fields using cut

00:50–01:00 · 10 minutes

### 5.1 What is cut?

`cut` extracts selected sections from each line of text.

It is particularly useful when records have predictable delimiters or character positions.

Syntax:

```bash
cut [OPTIONS] FILE
```

### 5.2 Understand delimiter-based extraction

Create a CSV file:

```bash
cat > ~/linux-training/day5/users.csv <<'EOF'
101,Dheeraj,Bengaluru,DevOps
102,Ravi,Mysuru,Developer
103,Anita,Mangalore,QA
104,John,Chennai,SRE
105,Meena,Bengaluru,Developer
EOF
```

Display:

```bash
cat ~/linux-training/day5/users.csv
```

Extract the first column:

```bash
cut -d ',' -f 1 ~/linux-training/day5/users.csv
```

Expected output:

```text
101
102
103
104
105
```

Explain:

- `-d ','` specifies the delimiter.
- `-f 1` selects the first field.

Extract the second column:

```bash
cut -d ',' -f 2 ~/linux-training/day5/users.csv
```

Extract multiple columns:

```bash
cut -d ',' -f 1,2 ~/linux-training/day5/users.csv
```

Extract the first and fourth columns:

```bash
cut -d ',' -f 1,4 ~/linux-training/day5/users.csv
```

Extract a range:

```bash
cut -d ',' -f 1-3 ~/linux-training/day5/users.csv
```

### 5.3 Extract characters by position

Create a sample file:

```bash
echo "LINUXDEVOPS" > sample.txt
```

Extract characters 1 to 5:

```bash
cut -c 1-5 sample.txt
```

Output:

```text
LINUX
```

### 5.4 Production scenario — extract usernames from a CSV

Imagine a report contains employee records, and the team needs only the usernames or IDs.

```bash
cut -d ',' -f 1 users.csv
```

This is useful for simple, consistently formatted files.

Important limitation: `cut` is not a full CSV parser. CSV files containing quoted fields with embedded commas require a proper CSV-aware tool.

## Part 6 — Sorting and removing duplicate records

01:00–01:15 · 15 minutes

### 6.1 sort — sort lines

Create a sample file:

```bash
cat > names.txt <<'EOF'
Ravi
Anita
Dheeraj
John
Meena
Anita
Ravi
EOF
```

Display:

```bash
cat names.txt
```

Sort alphabetically:

```bash
sort names.txt
```

Sort in reverse order:

```bash
sort -r names.txt
```

Sort numerically:

```bash
cat > numbers.txt <<'EOF'
100
20
3
50
9
EOF
```

Run:

```bash
sort -n numbers.txt
```

Explain:

Without `-n`, sorting is generally lexicographical rather than numerical.

For example, string sorting can place `100` before `20` because it compares characters rather than interpreting the values as numbers.

### 6.2 Sort by a particular field

Use the CSV file created earlier:

```bash
sort -t ',' -k 3 users.csv
```

Explain:

- `-t ','` sets the field delimiter.
- `-k 3` sorts using the third field.

This sorts records by city.

To sort numerically using the first field:

```bash
sort -t ',' -k 1,1n users.csv
```

### 6.3 uniq — identify adjacent duplicate lines

Explain an important concept:

`uniq` removes or reports adjacent duplicate lines. It does not automatically find all duplicate lines anywhere in a file.

Example:

```bash
cat names.txt
```

Output:

```text
Ravi
Anita
Dheeraj
John
Meena
Anita
Ravi
```

Run:

```bash
uniq names.txt
```

The repeated `Anita` and `Ravi` entries are not adjacent, so they remain.

Now run:

```bash
sort names.txt | uniq
```

This sorts the entries first, bringing duplicate lines together, then removes adjacent duplicates.

Expected output:

```text
Anita
Dheeraj
John
Meena
Ravi
```

### 6.4 Count duplicate occurrences

```bash
sort names.txt | uniq -c
```

Representative output:

```text
2 Anita
1 Dheeraj
1 John
1 Meena
2 Ravi
```

Sort the counts in descending numerical order:

```bash
sort names.txt | uniq -c | sort -nr
```

Explain:

- First `sort` groups identical names.
- `uniq -c` counts each group.
- Final `sort -nr` sorts the counts numerically in reverse order.

### 6.5 Production scenario — identify frequent application errors

Suppose a log contains repeated error messages.

You want to know which error appears most frequently.

```bash
grep "ERROR" app.log | sort | uniq -c | sort -nr
```

This is a basic example of log analysis using command-line tools.

Trainer note: In real production logs, timestamps may differ even when the underlying error is the same. Students will eventually need to extract the message field or normalise variable values before grouping. Today's example introduces the principle.

## Part 7 — Text transformation using tr and sed

01:15–01:30 · 15 minutes

### 7.1 tr — translate or delete characters

`tr` reads from standard input and translates or deletes characters.

Syntax:

```bash
tr [OPTIONS] SET1 [SET2]
```

It normally works with pipes or input redirection rather than accepting a filename argument directly.

Convert lowercase to uppercase:

```bash
echo "linux devops" | tr 'a-z' 'A-Z'
```

Output:

```text
LINUX DEVOPS
```

Convert uppercase to lowercase:

```bash
echo "LINUX DEVOPS" | tr 'A-Z' 'a-z'
```

Output:

```text
linux devops
```

Replace spaces with underscores:

```bash
echo "linux devops engineer" | tr ' ' '_'
```

Output:

```text
linux_devops_engineer
```

Delete digits:

```bash
echo "Server123Production456" | tr -d '0-9'
```

Output:

```text
ServerProduction
```

Squeeze repeated spaces:

```bash
echo "Linux     DevOps     Training" | tr -s ' '
```

Output:

```text
Linux DevOps Training
```

Explain:

- `-d` deletes specified characters.
- `-s` squeezes repeated occurrences.

### 7.2 sed — stream editor

`sed` processes text and performs transformations.

It is frequently used in automation scripts for simple text replacements, filtering and editing.

Replace text in output:

Create a file:

```bash
echo "APP_ENV=development" > environment.conf
```

Display a replacement:

```bash
sed 's/development/production/' environment.conf
```

Output:

```text
APP_ENV=production
```

Explain the syntax:

```bash
s/OLD/NEW/
```

- `s` means substitute.
- `OLD` is the text to find.
- `NEW` is the replacement text.

The original file remains unchanged because this command writes the transformed result to standard output.

Replace all occurrences on a line:

```bash
echo "dev dev dev" | sed 's/dev/prod/g'
```

Output:

```text
prod prod prod
```

Explain:

`g` means global replacement within each processed line.

Display only a particular line:

```bash
sed -n '2p' users.csv
```

Displays line 2.

Display lines 2 to 4:

```bash
sed -n '2,4p' users.csv
```

Explain:

- `-n` suppresses automatic printing.
- `p` prints the selected line or lines.

Production scenario — update a configuration value

A configuration template contains:

```text
APP_ENV=development
```

The deployment process needs to generate:

```text
APP_ENV=production
```

A preview command is:

```bash
sed 's/APP_ENV=development/APP_ENV=production/' app.conf
```

To save the replacement into a separate output file:

```bash
sed 's/APP_ENV=development/APP_ENV=production/' app.conf > app-production.conf
```

Production caution: Editing configuration files in place can be risky. Preview changes first, preserve backups, validate syntax and use a controlled deployment mechanism. `sed` replacement is not a safe general-purpose parser for YAML, JSON or complex configuration formats.

## Part 8 — Introduction to awk

01:30–01:45 · 15 minutes

### 8.1 What is awk?

`awk` is a powerful text-processing language used to process structured text, extract fields, perform calculations and generate reports.

It is particularly useful for:

- Processing application logs.
- Extracting selected columns.
- Calculating totals.
- Filtering records.
- Generating summaries.

Think of `awk` as a small data-processing tool available directly in the Linux terminal.

### 8.2 Understand how awk identifies fields

Consider this record:

```text
2026-11-04 10:01:12 ERROR user=103 action=payment status=failed
```

By default, `awk` treats whitespace as the field separator.

| Field | Value          |
| ----- | -------------- |
| $1    | 2026-11-04     |
| $2    | 10:01:12       |
| $3    | ERROR          |
| $4    | user=103       |
| $5    | action=payment |
| $6    | status=failed  |

Important variables:

- `$0` — entire input record.
- `$1` — first field.
- `$2` — second field.
- `$NF` — last field.
- `NF` — number of fields.
- `NR` — current record number.

### 8.3 Extract particular fields

Extract the date:

```bash
awk '{print $1}' ~/linux-training/day5/logs/app.log
```

Extract the time:

```bash
awk '{print $2}' ~/linux-training/day5/logs/app.log
```

Extract the log level:

```bash
awk '{print $3}' ~/linux-training/day5/logs/app.log
```

Extract the date, time and log level:

```bash
awk '{print $1, $2, $3}' ~/linux-training/day5/logs/app.log
```

### 8.4 Filter records using awk

Display only ERROR records:

```bash
awk '$3 == "ERROR" {print $0}' ~/linux-training/day5/logs/app.log
```

Explain:

- `$3` checks the third field.
- `==` compares values.
- `"ERROR"` is the required value.
- `{print $0}` displays the entire matching record.

Display only payment errors:

```bash
awk '$3 == "ERROR" && $5 == "action=payment" {print $0}' \
~/linux-training/day5/logs/app.log
```

Explain `&&` means AND.

### 8.5 Count error records using awk

```bash
awk '$3 == "ERROR" {count++} END {print count}' \
~/linux-training/day5/logs/app.log
```

Expected output:

```text
4
```

Explain the internal operation:

1. `awk` reads one record at a time.
2. It checks whether field 3 equals `ERROR`.
3. If true, it increments `count`.
4. After processing all records, `END` executes.
5. It prints the final count.

### 8.6 Process CSV data using awk

Our `users.csv` uses commas as delimiters.

Display the first and second columns:

```bash
awk -F ',' '{print $1, $2}' \
~/linux-training/day5/users.csv
```

Explain:

`-F ','` tells `awk` to use a comma as the field separator.

Display only developers:

```bash
awk -F ',' '$4 == "Developer" {print $2}' \
~/linux-training/day5/users.csv
```

Expected output:

```text
Ravi
Meena
```

### 8.7 Calculate a simple total

Create a salary file:

```bash
cat > salaries.txt <<'EOF'
Dheeraj 50000
Ravi 40000
Anita 45000
John 35000
EOF
```

Calculate total salary:

```bash
awk '{total += $2} END {print total}' salaries.txt
```

Expected output:

```text
170000
```

Calculate average salary:

```bash
awk '{total += $2; count++} END {print total/count}' salaries.txt
```

Expected output:

```text
42500
```

Trainer explanation: `awk` is not restricted to text searching. It can perform calculations and generate useful operational reports.

## Part 9 — Production troubleshooting challenge

01:45–01:55 · 10 minutes

Real-world DevOps exercise

Scenario: Investigating application failures

Your application team reports that users are experiencing payment failures.

You are given an application log containing thousands of records.

Your job is to identify:

1. Total number of ERROR records.
2. Failed payment transactions.
3. Unique user IDs associated with payment failures.
4. Most frequent error categories.
5. Time of the failures.

Use the log file created earlier.

Task 1 — Count errors

```bash
grep -c "ERROR" ~/linux-training/day5/logs/app.log
```

Expected:

```text
4
```

Task 2 — Find payment failures

```bash
grep "ERROR" ~/linux-training/day5/logs/app.log | grep "action=payment"
```

Expected:

```text
2026-11-04 10:01:12 ERROR user=103 action=payment status=failed
2026-11-04 10:01:30 ERROR user=105 action=payment status=failed
```

Task 3 — Extract user IDs

```bash
grep "ERROR" ~/linux-training/day5/logs/app.log |
grep "action=payment" |
awk '{print $4}'
```

Expected:

```text
user=103
user=105
```

Task 4 — Extract only the timestamps

```bash
grep "ERROR" ~/linux-training/day5/logs/app.log |
awk '{print $1, $2}'
```

Task 5 — Identify repeated error categories

```bash
grep "ERROR" ~/linux-training/day5/logs/app.log |
awk '{print $5, $6}' |
sort |
uniq -c |
sort -nr
```

Expected output:

```text
2 action=database status=timeout
2 action=payment status=failed
```

Task 6 — Save the results for investigation

```bash
grep "ERROR" ~/linux-training/day5/logs/app.log \
> ~/linux-training/day5/logs/errors-report.txt
```

Verify:

```bash
cat ~/linux-training/day5/logs/errors-report.txt
```

Explain that saving filtered results can help when preparing incident reports or sharing diagnostic evidence.

### 9.1 Introduction to xargs — an additional useful command

`xargs` builds command-line arguments from standard input.

For example, find all `.log` files and pass them to `wc -l`:

```bash
find ~/linux-training/day5 -type f -name "*.log" -print0 |
xargs -0 wc -l
```

Explain:

- `find` produces filenames.
- `-print0` separates filenames using a null character.
- `xargs -0` safely reads those filenames, including filenames containing spaces or newlines.
- `wc -l` counts lines in each file.

This is useful when working with many files.

Production caution: Be careful when combining `find`, `xargs` and commands that modify or delete files. First inspect the selected filenames before performing destructive operations.

## Part 10 — Day 5 knowledge check

Test your understanding

0/8 answered

1. Which command searches for files by name?

- `grep`
- `find`
- `sort`

2. Which `grep` option displays matching line numbers?

- `-c`
- `-v`
- `-n`

3. Which command extracts selected columns using a delimiter?

- `cut`
- `tail`
- `touch`

4. Why do we use `sort` before `uniq`?

- `uniq` requires adjacent duplicate lines
- `sort` encrypts the file
- `uniq` only works with CSV

5. Which command converts lowercase characters to uppercase?

- `sed`
- `tr`
- `wc`

6. In `awk`, what does `$0` represent?

- First field
- Last field
- Entire record

7. What does `NR` represent in `awk`?

- Number of records processed
- Number of files
- Last field

8. Which command replaces text in a stream?

- `sed`
- `mkdir`
- `stat`

Submit answers

## Day 5 homework

Complete the following exercises on your Ubuntu Linux environment.

1. Find all `.log` files under your home directory.
2. Find files larger than 10 MB.
3. Find files modified within the last 60 minutes.
4. Search a log file for `ERROR` and `WARN` entries.
5. Display matching lines with line numbers.
6. Count the number of failed transactions.
7. Extract the first and third columns from a CSV file.
8. Sort a list of employee names alphabetically.
9. Count duplicate entries using `sort` and `uniq`.
10. Convert lowercase text into uppercase using `tr`.
11. Replace `development` with `production` using `sed`, without changing the original file.
12. Use `awk` to count `ERROR` records and calculate an average from a numeric file.
13. Combine at least four commands using pipes to produce an application error report.

Bonus interview question: Explain the difference between `grep`, `sed` and `awk`. Give one real production example for each.
