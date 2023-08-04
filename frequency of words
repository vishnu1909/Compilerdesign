%{
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define MAX_WORD_LENGTH 100
typedef struct WordFrequency 
{
    char word[MAX_WORD_LENGTH];
    int frequency;
    struct WordFrequency* next;
} WordFrequency;
WordFrequency* head = NULL;
WordFrequency* findWordFrequency(const char* word) 
{
    WordFrequency* current = head;
    while (current != NULL)
{
        if (strcmp(current->word, word) == 0) 
{
            return current;
        }
        current = current->next;
    }
    return NULL;
}
void insertWordFrequency(const char* word)
{
    WordFrequency* existing = findWordFrequency(word);
    if (existing != NULL) 
{
        existing->frequency++;
        return;
    }
    WordFrequency* newWord = (WordFrequency*) malloc(sizeof(WordFrequency));
    strncpy(newWord->word, word, MAX_WORD_LENGTH);
    newWord->frequency = 1;
    newWord->next = head;
    head = newWord;
}
void printWordFrequencies() {
    printf("Word Frequency:\n");
    printf("----------------\n");
    printf("Word\t\tFrequency\n");
    printf("----------------\n");
    WordFrequency* current = head;
    while (current != NULL) {
        printf("%s\t\t%d\n", current->word, current->frequency);
        current = current->next;
    }
}
void cleanupWordFrequencies() 
{
    WordFrequency* current = head;
    while (current != NULL) {
        WordFrequency* temp = current;
        current = current->next;
        free(temp);
    }
}
%}
%option noyywrap
%%
[a-zA-Z]+ 
{
    char word[MAX_WORD_LENGTH];
    strncpy(word, yytext, MAX_WORD_LENGTH);
    word[MAX_WORD_LENGTH - 1] = '\0';
    insertWordFrequency(word);
}
\n 
{
    // Skip newline characters
}
. {
    // Skip any other character
}
%%
int main(int argc, char *argv[]) {
    yyin = stdin;
    yylex();
    printWordFrequencies();
    cleanupWordFrequencies();
    return 0;
}
********************************************************************************************************************************
Output:
C:\Users\harsh>set path=C:\Program Files (x86)\GnuWin32\bin

C:\Users\harsh>flex freq.l.txt

C:\Users\harsh>set path=C:\MinGW\bin

C:\Users\harsh>gcc lex.yy.c

C:\Users\harsh>a
enter: The sky is blue, rise is red.
word frequency:is=2
