---
title: "Milking the Yacc"
date: 2018-03-16T15:39:35+05:30
tags:
- compilers
- lex
- yacc
- how-to
- C
categories:
- project
---

So we had another assignment for our compilers construction course. We had already worked with lexical analyzers so this was a time for grammar parser generators. We had to create a BibTeX parser using Yacc/Bison. Here is a short introduction for anyone interested.

Yacc stands for Yet Another Compiler Compiler. It is a Look-ahead, Left-to-right parser generator. To know more about what parsers are, refer to a good compilers book (The Dragon Book, obviously!). GNU implements yacc in their program called Bison. Although, bison can be used in place of yacc, they are not completely the same and have small differences here and there.

Yacc generates a parser which goes through your program and checks it's syntax, extracts all useful information for compiling it and lots of other stuff. I used lex to tokenize the input. Yacc specifies what the tokens mean when taken together, much like how sentences are formed when words are placed in a certain order.

A simple yacc file follows the following order:
```c
%{
/* Header files */
/* Global variables, etc */
%}

/* Token declarations */

%%
/* Parsing grammar rules */
%%

/* C code */
```

Using `-d` option with yacc also generates a header file which contains an enum containing the tokens which can directly be used in the lex file to remove the redundant task of writing the writing the tokens again. Just include this file in lex and you're up!

This is all about passing the token name. But what about passing the token value to yacc? Well, that is done using a variable called `yylval`. This variable is of type `int` by default but yacc allows you to define it as a union in the "definitions" part.
```
%union {
    int   ival;
    char  *sval;
    float fval;
}
```
For passing strings from lex to yacc, it is important to remember to **copy** the contents from the token to `yylval` and not just pass it's address because it tends to get overwritten. This kept me up late because I kept getting segfaults which I could not figure out how!

The definitions block also contains the definitions of the tokens and the types of the sequences:
```c
%token  PLUS_SIGN DIGIT
%type   <ival>      add
```

The rules in yacc follow this simple pattern:
```c
/* Defines how numbers are formed */
integer:    DIGIT integer
            | DIGIT
            ;
```
To add two numbers, for example, you would write this:
```c
add:        integer PLUS_SIGN integer
                { /* This block contains the supporting C code */
                    $$ = $1 + $3;
                }
            ;
```
`$$`, `$1`, `$2`, etc. are special variable names which have their scopes within the rule only. `$$` is the variable associated with the current sequence. `$1` is the first token/sequence in the rule definition and so on.

The yacc file also contains the `main` function which calls `yyparse()` and a functions `yyerror(char *error)` which takes action according to the error. This is called by the generated parser when an error occurs while parsing.

The code for my project can be found here: [github.com/coditva/Yaccing](https://github.com/coditva/Yaccing).
