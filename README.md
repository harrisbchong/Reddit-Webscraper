# Inspired by 'I Gave My Goldfish $50,000 to Trade Stocks'
<p align="center">
  <a href="https://www.youtube.com/watch?v=USKD3vPD6ZA" target="_blank">
   <img src="https://img.youtube.com/vi/USKD3vPD6ZA/0.jpg" alt="Watch the video" width="640" height="480" border="10" />
  </a>
</p>


# Reddit-Webscraper

Simple Webscraper with PRAW (Python Reddit Api Wrapper) that scrapes the top weekly posts on r/CryptoCurrency. The script exports the post's data into either a Negative Posts.csv or Positive Posts.csv file based on a surface level sentiment analysis word bank, and also returns a list of scraped stock names to look for in the terminal. Helpful for keeping updated on crypto news and a basic general consensus on different coins.

# Process

To set up the PRAW account connection was fairly simple as I just had to create a script application on the reddit site and then connect it with PRAW in the code. The more interesting part was parsing through the information using separate word banks for the sentiment analysis. For each post it would parse through the title and the post description and look for the keywords in both banks and separate them into the according dictionary. The dictionaries would then be formatted using pandas and exported to .csv files.
