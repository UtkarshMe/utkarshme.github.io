---
title: "Learning Flex"
date: 2018-02-14T17:56:46+05:30
tags:
- compilers
- lex
- how-to
- C
categories:
- project
---

So we had this [assignment](https://github.com/coditva/Flexing) for our _Compilers Construction_ course to write a program to generated beautified HTML file for a given C program. The stupid approach is to write a lexical analyzer from scratch with might take ages. The intelligent (and accepted) approach is to use a lexical analyzer generator and this is where _Flex_ comes into picture.

Flex is a FOSS alternative to the POSIX lexical analyzer generator _Lex_ and generates a lexical analyzer program from the vocabulary you specify for the language you're writing a compiler for.

There are two parts to Flex, the definitions or _labels_ and the translations or _rules_. The rules section uses labels to simplify the rules. Both use _regex_ heavily (duh!).

A simple label looks like this. This puts the label `oreo` on all occurrences of the regex `(cat)` in the input.
```c
oreo        (cat)
```

A simple rules for the same looks like this. This replaces all occurrences of the label `oreo` in the input to `Oreo, the cat` in the output. The rules section is enclosed in two `%%`.
```c
{oreo}      { printf ("Oreo, the cat"); }
```

It should also have a `main` function which calls the `yylex()` function. A very simple flex file might look like this:

```c
/* Filename: simple.lex */
%option noyywrap

%{
/* I guess we do have to put labels on everything */
oreo        (cat)
adjective   (good|bad)
%}

%%
%{
/* You might not like them, but you need to have rules */
{oreo}      { printf ("Oreo, the cat"); }
{adjective} { printf ("lazy"); }
%}
%%

int main (int argc, char *argv[]) {
    yylex();
    return 0;
}
```

Compile it by:
```bash
flex simple.lex     # this will create lex.yy.c
gcc lex.yy.c        # this will create a.out
./a.out
```

On executing the `a.out` file and entering the input, you'll find the following output.
```text
input: this is cat
output: this is Oreo, the cat

input: cat is good.
output: Oreo, the cat is lazy.

input: nothing to do
output: nothing to do
```

You can find the code for the assignment [here](https://github.com/coditva/Flexing).
