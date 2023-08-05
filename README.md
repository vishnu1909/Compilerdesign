%{
#include <stdio.h>
%}

%%

[a-zA-Z]+    {
    printf("Word: %s\n", yytext);
}

[0-9]+    {
    printf("Number: %s\n", yytext);
}

[^a-zA-Z0-9 \n\t]+    {
    printf("Special character: %s\n", yytext);
}

[ \n\t]+   {/* Ignore whitespaces, newlines, and tabs */}

%%

int main(void) {
    yylex();
    return 0;
}

int yywrap(void) {
    return 1;
}
=======================================================================
OUTPUT:

