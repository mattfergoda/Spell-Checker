
# UW CLMS Application Work Sample
## Matt Fergoda
### A coding project submitted as a work sample for admission to UW CLMS in March 2020.


**Applicant**: Matt Fergoda  
**Course**: Harvard’s CS50: Introduction to Computer Science via EdX  
**Dates taken**: May - September 2019  
[**Link to full assignment description**](https://docs.cs50.net/2019/x/psets/4/speller/hashtable/speller.html)  

### Description
A simple spell checker. The program reads in a `.txt` file containing a list of correctly spelled words that acts as a dictionary. Each word is hashed and stored in a hash table. The program then reads in a separate `.txt` file and checks whether each word in the text appears in the dictionary, printing any "misspelled" words (i.e. words not in the dictionary) to the terminal.  

The assignment asked us to implement `dictionary.c` (containing the functions `hash`, `load`, `check`, `size`, and `unload`).  

`speller.c`, `speller.o`, `dictionary.h`, `dictionary.o`, and the `Makefile` were all included as part of the assignment’s distribution code.  

* `texts/` contains sample input texts.  
* `dictionaries/` contains one "small" and one "large" dictionary.  
* `output.txt` contains sample program output against the `holmes.txt` referencing the large dictionary.   
* `diff.txt` contains my program's output compared to the answer key's.  
* `keys/` contains answer keys for all texts referencing the large dictionary.   
### Usage
1. **Make sure you open the program in an environment with a bash shell**. Otherwise, `clang` will have trouble compiling during step 3. **If you would like to execute the program but don't have access to a bash shell environment,** the easiest workaround is to access the project in CS50’s proprietary IDE. To do so, please email me your GitHub username requesting access (unfortunately there's no option to make it public). Once I've granted you access, you can go to [this link](https://ide.cs50.io/mattfergoda/ide).

2. Navigate into the directory `UW_CLMS_Work_Sample`.

3. To have `clang` compile the program according to the `Makefile`’s specifications, run `make speller`.

4. The program’s usage is `./speller [dictionary] text`.
    * There are two dictionaries available with which to run the program: one “small” (with just two words) and one “large” (with several thousand words), both of which can be found in `dictionaries/`.
    * If the argument is omitted, the program will default to the large dictionary.
    * There are a variety of texts with which to run the program, found in `texts/`.
    * Answer keys demonstrating the correct program output using the large dictionary can be found in `keys/`.
    * For example, the command  
        '''<p style="text-align: center">./speller dictionaries/small texts/carroll.txt</p>```   
    will run the program on carroll.txt referencing the small dictionary while  
        ->```./speller dictionaries/large texts/holmes.txt```<-  
    or simply  
        ->```./speller texts/holmes.txt```<-  
    will run the program on holmes.txt referencing the large dictionary.
    * I suggest using
   ->``` ./speller [dictionary] text > output.txt```<-
    to print the output to a `.txt` file instead of the terminal, making it easier to compare the output to the key and keeping the terminal free of output.

5. To compare the output of my program to an answer key one can run, for example:
  -> ```
      ./speller texts/holmes.txt > output.txt
       diff -y output.txt keys/holmes.txt > diff.txt
    ```<-
    The output file `diff.txt` will print the program’s output for `holmes.txt` and the corresponding key side by side with `<` characters indicating lines that differ. Note that my program will have five lines of runtime information at the bottom of the output not included in the answer keys.  
    Here is example output from running the above command:
    ->```
    ...
    
   eBooks								eBooks
   PG								PG
   http								http
   tm								tm
   eBooks								eBooks
   eBooks								eBooks

   WORDS MISSPELLED:     17845					WORDS MISSPELLED:     17845
   WORDS IN DICTIONARY:  143091					WORDS IN DICTIONARY:  143091
   WORDS IN TEXT:        1150970					WORDS IN TEXT:        1150970
   TIME IN load:         0.04				      <
   TIME IN check:        0.74				      <
   TIME IN size:         0.00				      <
   TIME IN unload:       0.02				      <
   TIME IN TOTAL:        0.79				      <
   ```<-
