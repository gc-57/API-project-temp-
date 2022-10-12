# API-project

## Introduction

This is the final project for the course "Algoritmi e Principi dell'informatica" (API) from the second year of the bachelor in Cpmputer Science and Engineering at Polimi
(Politecnico di Milano).
Required knowledge for the project:
* sorting algoritms
* basic data structures like hash table, binary tree, RB trees, queues, stacks and lists (not all have been used)

## Description

You can find the original track (unfortunately only in italian) in the file "traccia.pdf", here a short summary in english:
* the goal of the project is to realize a program which check the correspondance between the letters of two words of the same lenght
* the word are sequences of the following characters:
  * lowercase alphabetic characters (a-z)
  * uppercase alphabetic characters (A-Z)
  * numbers (0-9)
  * underscore and minus ( _ , - )
* the program read from stdin a sequence of information and instruction and based on that produce some strings as output
  * read a value *k*, that's the lenght of the words
  * read a sequence (arbitrary lenght) of words, each one of lenght *k*, this is the set of allowable words (it doesn't contain duplicates)
* after that the program read a sequence of "games" each one marked by the command "+nuova_partita". After the new game command the program read:
  * the goal word for that game (lenght *k*)
  * *n* maximum number word to compare with the goal
  * a sequence of words to compare
* sometimes between the words can appear the command "+stampa_filtrate" (whose effect is described below)
* during a game or between tow can appear the commands "+inserisci_inizio" and "+inserisci_fine" and between them a sequence of words to be added to the allowable words
set (it's guaranteed it doesn't contain duplicates and that *k* is the lenght)
* for each word read "p", to be compared with the goal word "r" the program writes on stdout the following sequence o *k* chars (*res* is the output):
  * *res[i]* = '+' if *p[i]* = *r[i]* (*p[i]* is in the correct position)
  * *res[i]* = '/' if *p[i]* doesn't appear in *r*
  * *res[i]* = '|' if *p[i]* appear in *r* but not in position *i*; however if *p[i]* appear in *r* *m* times and the number of istances of *p[i]* that are in the correct
  place are *c* and before *p[i]* there are *m*-*c* chars equals to *p[i]* in the worng position then *res[i]* = '/'
* if the read word *p* is not part of the allowable words set the program must write on stdout "not_exists" and it doesn't count as a comparison
* if the program read the goal word *r* write on stdout "ok" and the game ends
* if the program read *n* word without the goal one the game end and the program write on stdout "ko"
* when a game end another can begin with the "+nuova_partita" command or a new sequence of words can be added to the set with the "+inserisci_inizio" command
* each comparison during a game produce some constrains, for example:
  > goal = abcabcabcabcabc   
  word = bbaabccbccbcabc   
  output = /+|+++|++/+++++ 
* from this comparison we learn that *b* is in position 2, 5, 8, 11, 14, there are only 5 *b* in the goal word (the 6th *b* originate a '/'), there are *c* in position
6, 9, 12, 15 and *c* can't be in position 7, 10 and there are only 5 *c* (same as *b* before), *a* is in position 4, 13 but not in position 3
* when during a game the command "+stampa_filtrate" appear the program must write on stdout (in ascii order) all the words from the allowable words set which respect the
constrains learned with all the previous comparisons
* during a game after each comparison the program must write on stdout the number of the allowable words which respect the constrains learned

## Other informations

In this repo you can find other than my code for the project a folder called "opentestcases" which contain 5 input with the corresponding output, this were the ones
provided by the professor to test our program, the real inputs used for the valutation are unknown.
If you want other larger input files you can check this public repo by my friends dudoleitor https://github.com/Dudoleitor/API_WordChecker-Public_tests.git
