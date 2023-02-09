Trailing semicolons
===================


Semicolons in q are *separators*. 

In a *script*, newlines also separate expressions to be evaluated.

```q
a:b:100; c:42
sqr:{x*x}
```

This is not so in a multiline lambda, where expressions can be separated only with semicolons.

```q
foo:{
  a:b:100; c:42;
  sqr:{x*x};
  b*c+sqr x}
```

In a script, a trailing semicolon suggests an assignment is part of the definition of a lambda or a list.
Spare your reader the cognitive burden of discovering that they are not.

**Do not suffix script lines with redundant semicolons.**

Legitimate uses for a trailing semicolon
----------------------------------------
Where the expression’s important work is a side effect, suffixing a semicolon clearly discards any result.

```q
update c:a+b from `t;  /discard `t
-1 "Hello world";      /discard -1
initialize[];          /discard any result
```

In the last example, `initialize` might have returned a result bound for stdout. 
Suffixing a semicolon makes it clear that any result is discarded. 

This is helpful even where a ‘no result’ lambda returns a general null `::`, which is not displayed.

```q
q)f:{exp1;exp2;}     / no result
q)(::)~f[]           / is actually a null
1b
q)f[]                / that we don't see
q)f[];               / but whatever it is we don't want it
```

