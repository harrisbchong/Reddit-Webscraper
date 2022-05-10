from curses.ascii import isupper
import praw
import pandas as pd

# Read-only instance
reddit_read_only = praw.Reddit(client_id="",		 # your client id
                               client_secret="",	 # your client secret
                               user_agent="")	 # your user agent

subreddit = reddit_read_only.subreddit("CryptoCurrency")

posts = subreddit.top("week")
# Scraping the top posts of the current month

# Store positive posts
positive_posts_dict = {"Title": [], "Post Text": [],
                       "Score": [], "Total Comments": [], "Post URL": []}

# Store negative posts
negative_posts_dict = {"Title": [], "Post Text": [],
                       "Score": [], "Total Comments": [], "Post URL": []}

# Tentative list of words for sentiment analysis
# List of Positive Words to filter
positive_words = ['up', 'hold', 'HODL', 'buy', 'dip', 'gains', ]

# List of Negative Words to filter
negative_words = ['down', 'sell', 'sold',
                  'scam', 'dump', 'pump', 'drops', 'falls', 'loss', 'low']


def append(dict):
    # Title of each post
    dict["Title"].append(post.title)

    # Text inside a post
    dict["Post Text"].append(post.selftext)

    # The score of a post
    dict["Score"].append(post.score)

    # Total number of comments inside the post
    dict["Total Comments"].append(post.num_comments)

    # URL of each post
    dict["Post URL"].append(post.url)


companies = []

for post in posts:
    status = 0

    # List of Stock names
    for word in (post.title.split() or post.selftext.split()):
        if (word not in companies and (len(word) == 3 or len(word) == 4) and word.isupper() and word.isalpha()):
            companies.append(word)

    for word in negative_words:
        if (word in (post.title or post.selftext)):
            append(negative_posts_dict)
            status = 1
            break

    if status == 0:
        for word in positive_words:
            if(word in (post.title or post.selftext)):
                append(positive_posts_dict)
                break

# Saving the data in a pandas dataframe
positive_posts = pd.DataFrame(positive_posts_dict)

negative_posts = pd.DataFrame(negative_posts_dict)

# Export data to csv files
positive_posts.to_csv("Positive Posts.csv", index=True)
negative_posts.to_csv("Negative Posts.csv", index=True)

print(companies)
print("Web Extraction complete.")
