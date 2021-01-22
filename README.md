# latex-json

This is a latex style file which define a macro of a perser of JSON.

This style file requires `catchfile.sty`,
which is contained in
TeXLive and MiKTeX as catchfile.

## How to use

If you want to read a JSON file `suplement.json` from the main file `main.tex`,
then do the following:
* Add `\usepackage{json}` in preamble of `main.tex`.
* Add `\inputjson{xxx}{suplement.json}` in `main.tex`.

If `suplement.json` is
```
{"x":"a",
 "y":{"X":"b"},
 "z":["c","d"]}
```
then you can obtain the terminal strings `a`, `b`, `c`, and `d` by
```
\jsondata{xxx->x}
\jsondata{xxx->y->X}
\jsondata{xxx->z->0}
\jsondata{xxx->z->1}
```
respectively.

A terminal literal is 
a sring, number, boolean, or null.
At this moment,
numbers, booleans, and null are
just strings.
For example,
the boolean value `true` is
not `\iftrue` but `true`.
At this moment,
backslash escaping of strings is ignored.
For example.
`"a\nu"` is not `a\\u` but `a\nu`.

