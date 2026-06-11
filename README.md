# raven-table

Renders rows as an aligned text table. Columns size themselves to their widest
cell, the header is bold, and short rows are padded out. It uses raven-color for
the bold header.

## Install

```toml
[dependencies]
"github.com/martian56/raven-table" = "0.1"
```

That pulls in raven-color as well.

## Usage

```raven
import "github.com/martian56/raven-table" { Table }

let t = Table.new(["Name", "Age", "City"])
t.row(["Alice", "30", "New York"])
t.row(["Bob", "25", "Boston"])
print(t.render())
```

which lays out as (the header bold, not shown here):

```
Name   Age  City
-----  ---  --------
Alice  30   New York
Bob    25   Boston
```

For a file or a pipe where you don't want the escape codes, build the table with
`.plain()`:

```raven
Table.new(["A", "B"]).plain()
```

## How it works

`Table.new(headers)` starts a table, `row(cells)` adds a row (and returns the
table, so you can chain the calls or not), and `render()` hands back the string.
A short row leaves its missing cells blank, and no line ends with trailing
whitespace.

## License

MIT
