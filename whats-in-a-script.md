What’s in a script?
===================


A script template used by one programmer consists of the following sections:

```q
\l subscript.q          / load subscripts
…

\e 1                    / global state-settings
…

\d .chunk               / carve out a chunk of the tree

foo:{                   / define functions
…

Var:…                   / define variables
```
