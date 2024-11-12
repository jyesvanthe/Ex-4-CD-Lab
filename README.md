# Ex-4-LETTER-FOLLOWED-BY-ANY-NUMBER-OF-LETTERS-OR-DIGITS-USING-YACC-USING-YACC
RECOGNITION OF A VALID VARIABLE WHICH STARTS WITH A LETTER FOLLOWED BY ANY NUMBER OF LETTERS OR DIGITS USING YACC
# Date:11-11-2024
# Aim:
To write a YACC program to recognize a valid variable which starts with a letter followed by any number of letters or digits.
# ALGORITHM
1.	Start the program.
2.	Write a program in the vi editor and save it with .l extension.
3.	In the lex program, write the translation rules for the keywords int, float and double and for the identifier.
4.	Write a program in the vi editor and save it with .y extension.
5.	Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l
6.	Compile the yacc program with YACC compiler to produce output file as y.tab.c. eg $ yacc –d arith_id.y
7.	Compile these with the C compiler as gcc lex.yy.c y.tab.c
8.	Enter a statement as input and the valid variables are identified as output.
# PROGRAM
Grammer.|
```
%{
#include "y.tab.h"
%}

%%
a    { return A; }  // Recognize 'a' as token A
b    { return B; }  // Recognize 'b' as token B
.    { return 0; }  // End of input
%%

int yywrap() {
    return 1;
}
```
Grammer.y
```
%{
#include <stdio.h>
int yylex(void);
void yyerror(const char *s);
%}

%token A B

%%
S   : A A A A A A A A A A B    { printf("Valid string\n"); }
    | A S B                    { printf("Valid string\n"); }
    ;

%%

int main() {
    printf("Enter a string:\n");
    yyparse();
    return 0;
}

void yyerror(const char *s) {
    printf("Invalid string\n");
}
```
# Output
![379106648-238350e9-88b9-40aa-851e-101cbc1cae3e](https://github.com/user-attachments/assets/e3b581d8-e279-487e-ab47-af2c5d73f89e)
# Result
A YACC program to recognize a valid variable which starts with a letter followed by any number of letters or digits is executed successfully and the output is verified.
