# PREDICTING TRACK SUCCESS ON SPOTIFY USING COVER ART

A picture is said to be worth a thousand words, but does that saying still apply to album art? Before streaming services such as Spotify became the preferred format for music consumption, listeners would peruse the aisles of music stores, scanning the album artwork of CD's and Vinyl Records. During this time, album art likely played a role in whether the album was purchased or not. Our goal is to predict whether this still is true, and if so, determine which album covers are predicted to be most sucessful.

   ![alt text](/images/cover_art_banner.jpeg)

# Business Understanding

<!--  Nowadays, music marketing companies and design services are assuring the world that album art still plays a role in the success of the album and artists' music, but without backing.  -->

Album art has played an important role in music. It gives visual representation and additional context to the story behind an album. Perhaps most importantly, it helped artists sell music. Before streaming was introducted into the world of music, albums were largely judged by their artwork. Iconic albums such as "Abbey Road" by The Beatles and "Nevermind" by Nirvana have artwork that are still frequently talked about today. 


* maybe add something here about kanye expensive album focused on album artwork . leaves people wondering where to allocate resources

However, in recent years streaming services such as Spotify have dominated, with streaming making up [80% of revenue](https://toneisland.com/music-industry-statistics/) in the U.S. music industry. Artists and labels have been left wondering if this shift from hard copies to streaming has affected the prominence of albums, and therefore album artwork. [The Playist Effect](https://blog.landr.com/album-art-absolutely-crucial-success-2016/) is a phenomenon that suggests with the rise of streaming, subscribers largest listen to curated auto-play playlists with individual tracks rather an albums as a whole. 

with Spotify leading the music streaming industry, it's crucial for record labels to understand the effectiveness of albums and their artwork in this space. 

This analysis will look at the popularity of tracks from Spotify's discovery playlists and their respective artwork to determine which album styles are associated with track success. 


<!-- problem with spotify metric: https://medium.com/analytics-vidhya/determining-popularity-of-rising-pop-artists-with-scraped-spotify-data-and-nlp-sentiment-analysis-f62aa182f5fe -->

Skips:
(https://musicmachinery.com/2014/05/02/the-skip/)

Spotify is the largest music streaming service:
https://toneisland.com/music-industry-statistics/

# Data Understanding

Data for this project was pulled from the Spotify API [Spotipy](https://spotipy.readthedocs.io/en/master/), however the data pulled for this analysis has also been saved in the [data folder]() of this repo. 

The input variables are 1,835 album artworks from tracks in Spotify's "Fresh Finds" playlists. These playlists are solely comprised of independent artists and labels to eliminate potential outliers from hugely sucessful artists who will likely generate many streams regardless of album art. 

the target variable is the track's popularity index, an integer between 0 and 100, with 100 being most popular. This is [defined as](https://developer.spotify.com/documentation/web-api/reference/#/operations/get-several-tracks) "The popularity is calculated by algorithm and is based, in the most part, on the total number of plays the track has had and how recent those plays are. Generally speaking, songs that are being played a lot now will have a higher popularity than songs that were played a lot in the past."

# Data Processing

For model input each album artwork was imported and resized to a 3 dimensional shape of (60, 60, 3), where each value in the height and width represents a pixel of the image, and the depth represents the R, G, B color values of the image. 

![](/images/album_example.png) ![](/images/album_example2.png) ![](/images/album_example3.png) 


# Modeling and Evaluation

Convolutional Neural Networks were chosen for this Image Classification Regression analysis.


<!-- What kind of model(s) did you use?
How well did your final model perform, compared to the baseline? -->

# Conclusion
<!-- How would you recommend that your model be used? -->



recs - If album art is important to you, consider launching artists in vinyl, as this has seen a rise in sales, especially among the younger demographic

# Repository Navigation
An explanation of the repository organization
Links to the final notebook and presentation
As a reminder, the Markdown notation for a link is 
[link text](/path/to/file)
**Reproduction instructions (or a link to them)



# Repository Structure

```
├── data : data used for modeling
├── images : images used in PPT and readme
├── README.md : project information and repository structure
├── dsc-capstone-project.pptx : (Presentation for Stakeholders)
└── dsc-capstone-project.ipynb (jupyter notebook used for modeling)
```
