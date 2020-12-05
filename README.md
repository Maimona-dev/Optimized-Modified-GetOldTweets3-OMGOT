# Optimized-modified-GetOldTweets3-OMGOT
GetOldTweets-Python is a project written in Python to mine old and backdated tweets, It bypasses some limitations/restrictions of the Twitter API. This Repo houses an improvement fork of the original GetOldTweets Library by [Jefferson Herique](https://github.com/Jefferson-Henrique/GetOldTweets-python). The improvement makes running this package on Windows OS seamless with Python 3.x. 


 ## Details
Before coming here to get backdated timeline tweets, you might have gone to Twitter to create a Developer account, before the sad reality dawns on you that you can not mine tweets older than 7 days, using twitter's rest API, unless you pay and even when you do, you are restricted to a limit of 100 tweets daily. Just how slow would that be if you intend to mine say 10 years worth of textual big data for data analysis. You might have also tried "Googling" some other methods to mine old tweets, you might have seen different sites, libraries or tools you didnt know how to use, and all sorts of confusing information on the web. This modified getoldtweets3 library helps you download backdated-timeline twitter data easily and without hassles from command line, either on windows OS, ubuntu-linux OS, or Mac OS. You only need to have python installed on your machine as the primary prerequisite. You also need to set the environment variable path for Python or better still, install Python in such a way that you can call it from the command line or Terminal. [check here to see how you can do that easily](https://stackoverflow.com/posts/54934172/)


## Prerequisites
This packages assumes you are running python version 3.x on your local machine, and that you have already set the python environment variable path, so you can interactively fire up python from command prompt or terminal without getting any error. If you haven't, kindly follow this [stackoverflow answer](https://stackoverflow.com/questions/3701646/how-to-add-to-the-pythonpath-in-windows-so-it-finds-my-modules-packages) for guidance, [you might want to take a look at this too for more clarity](https://stackoverflow.com/posts/54934172/edit). 

After getting that right and out of the  way, the next major python packages you need to install are pyQuery, and Lxml for handling requests and xml/html documents. That could be easily done on cmd or on terminal by - just typing `pip install pyquery` once that is done, then you do `pip install lxml`   


## Components
- When you run this package from command line, it typically returns the following as columns in an output.csv file that would be saved in your current working directory. It should be noted that the geo attribute returns an empty column. So if you need to get location based twitter user data, you would have to specify the Geographical coordinates as well as the search radius. 

  - id (str)
  - permalink (str)
  - username (str)
  - text (str)
  - date (date)
  - retweets (int)
  - favorites (int)
  - mentions (str)
  - hashtags (str)
  - geo (str)


## Command Line Arguments

This package was optimized to work more efficiently and seamlessly on both Windows Command prompt (CMD), and on UNIX Terminal. The following are their associated command line arguments. 


  - username (**str**): An optional specific username from a twitter account. Without "@".
  - since (**str. "yyyy-mm-dd"**): A lower bound date to restrict search.
  - until **(str. "yyyy-mm-dd"**): An upper bound date to restrist search.
  - querysearch (**str**): A query text to be matched.
  - toptweets (**bool**): If True only the Top Tweets will be retrieved.
  - near(**str**): A reference location area from where tweets were generated.
  - within (**str**): A distance radius from "near" location (e.g. 15mi).
  - maxtweets (**int**): The maximum number of tweets to be retrieved. If no number is set here or is lower than 1 all possible tweets will be retrieved.


## Usage - Very Important to Understand.

1. Clone or download the repo to your local machine.
2. Unzip it.
3. cd to the unzipped Optimized-Modified-GetOldTweets3-OMGOT-master folder
4. cd again to the GetOldTweets3-0.0.10 folder inside unzipped Optimized-Modified-GetOldTweets3-OMGOT-master folder, and fire up command prompt or terminal right there. 
5. then run the codes in the examples below. 

Please Feel free to customize, change the parameters/arguments as used in the examples below according to the needs of your project. 

## Use Cases

**Use case 1 - Get the most recent 100 top tweets by username:**

```
python GetOldTweets3.py --username "mo4president" --toptweets --maxtweets 100
```
Specified ```--username```, ```--toptweets```, and ```--maxtweets``` Which was set to 100. Meaning to retrieve the last 100 toptweets from twitter, made by that username. 

**Use case 2 - Get 500 tweets by the username and bound dates**:
```
python GetOldTweets3.py --username "SOdaibo" --since 2017-05-10 --until 2019-05-10 --maxtweets 500
```
Specified ```--username```, ```--since```, ```--until```, and ```--maxtweets``` Which in this case was set to 500. And the above command retrieves 500 tweets made by the username given fromm May 2017 till May 2019 (2 years worth.)

**Use case 3 - Get tweets by language and keyword search:**
```
python GetOldTweets3.py --querysearch "football" --lang es --maxtweets 100
```
Specified ```--querysearch```, ```--lang```, and ```--maxtweets```, Which in this case was set to 100. And the above command retrieves 100 tweets data from twitter that has the keyword "football" in it. The language parameter here was set to spanish 'es', meaning only spanish tweets are stored. By default, the code retrieves all the tweets found on the querysearch keyword irrespective of the language. The language parameter acts more like a runtime preprocessing step to seive out unwanted contents. 'en' - English, 'cn'- Chinese. 

**Use case 4 - Get 500 tweets by querysearch and geo coordinates:**
```
python GetOldTweets3.py --querysearch "BBNaija" --near "6.52, 3.37" --within 40km --maxtweets 500
```
Specified ```--querysearch```, ```--near```, ```--within```, and ```--maxtweets``` Which in this case was also set to 500. And the above command retrieves 500 tweets data from twitter that has the keyword BBNaija, within a 40km radius of the grographical coordinate given, which happened to be Lagos Island, Lagos state, Nigeria. 




### Update (18-09-2020): 

This tool is currently broken because twitter made an upgrade to their API endpoints from V1.1 to V1.2, and as a result of that, some of the endpoints used in this tool became deprecated. [Here's some more details on their new API](https://blog.twitter.com/developer/en_us/topics/tips/2020/understanding-the-new-tweet-payload.html). 
I will be working to fix this and get this tool up and running ASAP, because I know a number of individuals usiing this tool for their academic thesis and personal/learning projects. 

### Update (12-10-2020): 
Things moved pretty fast, I apologise for the silence. I have been quite busy on my end. There is an alternative tool I made use of today with slight modification to the CLI use-case (I am big fan of the terminal, and wriiting less code). Its called Twint, I think it serves the same purpose as this tool and more (IT is very RICH!). Here's a link to the [github repo for Twint](https://github.com/marquisvictor/twint). 

Here's the little modification I did:
- After cloning the repo, I navigated to the Twint folder and looked for a ```cli.py``` file. 
- I copied it and moved it one level outside the twint folder. 
- once outside the Twint folder, I opened it and commented out the previous imports and added mine. Just like it is below.
```
# from . import run
# from . import config
# from . import storage

from twint import *
```
- Then I opened terminal in the same folder where I have the ```cli.py``` file and run the first command on their [github readme](https://github.com/marquisvictor/twint/blob/master/README.md). Only replacing the `twint` with `python cli.py` and the username with my own. As shown below:

`python cli.py -u irekponorvictor`

This worked very well for me, The Twint tool is also actively maintained at the moment. So If you find yourselves here, and I've not rectified this (optimizedGetOldTweets) tool yet, Twint tool would definitely work for your use-case. I would go ahead to update the medium post now. 

#### [Feel free to connect with me on linkedIn](https://www.linkedin.com/in/victor-e-irekponor-a926a1154/).
#### [Twitter](https://twitter.com/IrekponorVictor).
#### [Read my latest write-ups on medium](https://medium.com/@IrekponorVictor).
