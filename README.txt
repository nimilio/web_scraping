

The wiki_query.py consists of a function that retrieves the wikipedia text from a specific search term. In this case, we make no use of API.

We can call this function from the command line using the sys.argv array, such as:

python wiki_query.py term

For example:

python wiki_query.py Sweden


In order to do that, we assign sys.argv[1] (the second element of the sys.argv array) to the term variable.

Since this program scrapes data from Wikipedia only, the function includes the wikipedia address. In case our given term consists of special characters (ASCII) these are replaced with the method urllib.parse.quote. What is really interesting with this method is that it may be possible sometimes  to pass a term in non-english/latin language, but still print the wikipedia text of this term. For instance, you can try the word "Αθήνα" (Athens in Greek) and see what happens.

We used the urllib.request.urlopen to open the wikipedia page of this specific term, but in case the search term that we pass does not exist, is misspelled etc., an error is raised and the program exits. If the term exists, a beautiful soup object is created, which includes the string of the url and the "lxml" parser. Finally, the program loops and extracts all data with a "p" (paragraph") tag and the text is printed.