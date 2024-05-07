# Ex-6-LETTER-FOLLOWED-BY-ANY-NUMBER-OF-LETTERS-OR-DIGITS-USING-YACC-USING-YACC
RECOGNITION OF A VALID VARIABLE WHICH STARTS WITH A LETTER FOLLOWED BY ANY NUMBER OF LETTERS OR DIGITS USING YACC
# Date:
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
```
Program name:ex5.l
%{
/* This LEX program returns the tokens for the expression */
#include "y.tab.h"
%}
%%
"=" {printf("\n Operator is EQUAL");}
"+" {printf("\n Operator is PLUS");}
"-" {printf("\n Operator is MINUS");}
"/" {printf("\n Operator is DIVISION");}
"*" {printf("\n Operator is MULTIPLICATION");}
[a-zA-Z]*[0-9]* {
printf("\n Identifier is %s",yytext);
return ID; }
. return yytext[0];
\n return 0;
%%
int yywrap()
{
return 1;
}
Program name:ex5.y
%{
#include<stdio.h>
/* This YACC program is for recognizing the Expression */
%}
%token A ID
%%
statement: A'='E
| E {
printf("\n Valid arithmetic expression");
$$=$1;
}
;
E: E'+'ID
| E'-'ID
| E'*'ID
| E'/'ID
| ID
;
%%
extern FILE*yyin;
main() {
do {
yyparse();
}while(!feof(yyin)); }
 yyerror(char*s)
{
}
```
# Output
![328529342-b0ea3694-6956-4abf-b8af-8c6e35d93ede](https://github.com/Swetha733N/Ex-6-LETTER-FOLLOWED-BY-ANY-NUMBER-OF-LETTERS-OR-DIGITS-USING-YACC-USING-YACC/assets/122199934/3da8c0d7-3462-4d09-b014-bbc8bca5a483)

# Result
A YACC program to recognize a valid variable which starts with a letter followed by any number of letters or digits is executed successfully and the output is verified.


