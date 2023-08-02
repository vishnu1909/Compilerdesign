%{
%}
%%
[a-z A-z 0-9 _]+"@"[a-z]+".com" {printf("\nvalid email\n");}
.+ {printf("\ninvalid email\n");}
%%
int yywrap(void){}
int main()
{
printf("\nenter email : ");
yylex();
printf("\n");
return 0;
}
