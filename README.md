# latex-json

This is a latex style file which define a macro of a perser of JSON.

This style file requires `catchfile.sty`,
which is contained in
TeXLive and MiKTeX as catchfile.

## How to use

If you want to read a JSON file `suplement.json` from the main file `main.tex`,
then do the following:
* Add `\usepackage{json}` in preamble of `main.tex`.
* Add `\inputjsondata{xxx}{suplement.json}` in `main.tex`.

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
backslash escaping of strings is ignored.
For example.
`"a\nu"` is not `a\\u` but `a\nu`.

At this moment,
numbers is just strings.
The numbers is not counter nor length nor dimension.

Booleans `true` and `false`  are strings defined by
```
\newcommand{\nu@json@literal@true}{true}
\newcommand{\nu@json@literal@false}{false}
```
respectively.
You may use `\renewcommand{\nu@json@literal@true}{\iftrue}` to
change form string to `\iftrue`.

The JSON literal `null` is a string defined by
```
\newcommand{\nu@json@literal@null}{null}
```

At this moment,
this style file does not work for
JSON files containing the following:
* keys containing the string `->`
* backslash-escaped keys
