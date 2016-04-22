Start of some tools around pasting MySQL/Text output and getting that in more useful outputs, e.g. a comma-separated-list.

## Installation

Currently only via git:

```
git clone git@github.com:robballou/paste-table-util.git
pushd paste-table-util
npm install
popd
```

## Usage

❗**Very alpha**. Expect the unexpected, random console logs, etc.

```
echo '| 1234 |
| 5678 |' | node bin.js

cat some_db_output.txt | node bin.js --tab-delimited
cat some_db_output.txt | node bin.js --column 0

# on mac: paste & copy the table output
pbpaste | paste-table | pbcopy
```

## Command line options

### tab-delimited

`-t`  
`--tab-delimited`

Return results delimited by tab. Used only if there are multiple columns in each
line.

### column

`-c <n>`  
`--column <n>`

Return a specific column specified by a zero-based index (column 1 = 0, etc.).
Only works on multiple column data and will only return results for columns
that have that many columns. For example, this data will have 2 results for `column=1`:

```
123|456
789|012
555
```

### list

`-l`  
`--list`

Used when you are selecting a column this can be used to compress it to a comma
delimited list. By default, when you're not selecting a column, this is expected
behavior ... but when you select columns, we keep everything as rows.

```
123|456
789|012
555
```
