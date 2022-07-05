# web_scraping
Two simple web scraping scripts for twitter and wikipedia


Twitter


The twitter_query.py consists mainly of:

1) a set of credentials for user authentication, from which we instantiated the Tweeter API and created the API object

2) one function that executes the task

3) and one "if statement" that handles how to call the function



We can execute this script using the sys.argv method:

python twitter_query.py profile_name number_of_tweets


For example:
python twitter_query.py tomhanks 3


sys.argv is an array of command line options, where the first element (sys.argv[0]) is  the name of the script and the rest of the elements are the arguments that we pass to the function/command line. These arguments are the name of the twitter profile and the date/number of the tweets we want to scrape. The latter argument though is optional.


So, when we pass two arguments in command line (tomhanks 3), then the sys.argv array consists of three elements (sys.argv[0], sys.argv[1] and sys.argv[2]). If we pass only the profile name, then the array consists of two arguments. Thus, we call the function based on an "if statement" that handles these cases, otherwise it would yell a list index error, in case we used only one argument.

When it comes to the function per se, in case we pass the second argument, we have to turn it into an integer (because now it is a string) to check if it is bigger than 0. In this case, the program will loop through the tweets of this profile and will print the number of tweets that we specified (using the api.user_timeline method). If the integer is 0, it will return no tweet and if the integer is negative, the program will print an error.

In case though the second argument is not specified, then the None type object is not considered to be an integer, thus we use this case as an exception so that no error is raised. We loop through tweets and print only the first-latest tweet of this profile.


The emojis of the tweets are printed, but retweets and replies not. If an image is included in the tweet, the url of this image is shown.



Wikipedia



The wiki_query.py consists of a function that retrieves the wikipedia text from a specific search term. In this case, we make no use of API.

We can call this function from the command line using the sys.argv array, such as:

python wiki_query.py term

For example:

python wiki_query.py Sweden


In order to do that, we assign sys.argv[1] (the second element of the sys.argv array) to the term variable.

Since this program scrapes data from Wikipedia only, the function includes the wikipedia address. In case our given term consists of special characters (ASCII) these are replaced with the method urllib.parse.quote. What is really interesting with this method is that it may be possible sometimes  to pass a term in non-english/latin language, but still print the wikipedia text of this term. For instance, you can try the word "Αθήνα" (Athens in Greek) and see what happens.

We used the urllib.request.urlopen to open the wikipedia page of this specific term, but in case the search term that we pass does not exist, is misspelled etc., an error is raised and the program exits. If the term exists, a beautiful soup object is created, which includes the string of the url and the "lxml" parser. Finally, the program loops and extracts all data with a "p" (paragraph") tag and the text is printed.
