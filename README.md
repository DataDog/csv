# csv

[![Godoc](http://img.shields.io/badge/godoc-reference-blue.svg?style=flat)](https://godoc.org/github.com/DataDog/csv) [![license](http://img.shields.io/badge/license-BSD-red.svg?style=flat)](https://raw.githubusercontent.com/DataDog/csv/master/LICENSE)

fork of go's encoding/csv with extra writer options

## install

```sh
go get github.com/DataDog/csv
```

## usage

The main addition to `encoding/csv` is the added added `UnquoteEmpty` option on
Writers:

```go
type Writer struct {
    Comma        rune // Field delimiter (set to ',' by NewWriter)
    UseCRLF      bool // True to use \r\n as the line terminator
    UnquoteEmpty bool // True to not quote empty fields
}
```

This option allows you to forgo quotes on empty fields, which makes its output
compatible with some CSV SQL dumps that differentiate between "", a blank string,
and a completely empty field, which means NULL.
