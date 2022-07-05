
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

