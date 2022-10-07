# PREDICTING TRACK SUCCESS ON SPOTIFY USING COVER ART

A picture is said to be worth a thousand words, but does that saying still apply to album art? Before streaming services such as Spotify became the preferred format for music consumption, listeners would peruse the aisles of music stores, scanning the album artwork of CD's and Vinyl Records. During this time, album art likely played a role in whether the album was purchased or not. Our goal is to predict whether this still is true, and if so, determine which album covers are predicted to be most sucessful.

   ![alt text](/images/cover_art_banner.jpeg)

# Business Understanding

<!--  Nowadays, music marketing companies and design services are assuring the world that album art still plays a role in the success of the album and artists' music, but without backing.  -->

Album art has played an important role in music. It gives visual representation and additional context to the story behind an album. Perhaps most importantly, it helped artists sell music. Before streaming was introducted into the world of music, albums were largely judged by their artwork. Iconic albums such as "Abbey Road" by The Beatles and "Nevermind" by Nirvana have artwork that are still frequently talked about today. 

However, in recent years streaming services such as Spotify have dominated, with streaming making up [80% of revenue](https://toneisland.com/music-industry-statistics/) in the U.S. music industry. Artists and labels have been left wondering if this shift from hard copies to streaming has affected the prominence of albums, and therefore album artwork. [The Playist Effect](https://blog.landr.com/album-art-absolutely-crucial-success-2016/) is a phenomenon that suggests with the rise of streaming, subscribers largest listen to curated auto-play playlists with individual tracks rather an albums as a whole. 

with Spotify leading the music streaming industry, it's crucial for record labels to understand the effectiveness of albums and their artwork in this space. 

This analysis will look at the popularity of tracks from Spotify's discovery playlists and their respective artwork to determine which album styles are associated with track success. 



Skips:
(https://musicmachinery.com/2014/05/02/the-skip/)

Spotify is the largest music streaming service:
https://toneisland.com/music-industry-statistics/

# Data Understanding

Data for this project was pulled from the Spotify API [Spotipy](https://spotipy.readthedocs.io/en/master/), however the data pulled for this analysis has also been saved in the [data folder]() of this repo. 

The input variables are 1,835 album artworks from tracks in Spotify's "Fresh Finds" playlists. These playlists are solely comprised of independent artists and labels to eliminate potential outliers from hugely sucessful artists who will likely generate many streams regardless of album art. 

the target variable is the track's popularity index, an integer between 0 and 100, with 100 being most popular. This is [defined as](https://developer.spotify.com/documentation/web-api/reference/#/operations/get-several-tracks) "The popularity is calculated by algorithm and is based, in the most part, on the total number of plays the track has had and how recent those plays are. Generally speaking, songs that are being played a lot now will have a higher popularity than songs that were played a lot in the past."

# Modeling and Evaluation

For model input each album artwork was imported and resized to a 3 dimensional shape of (60, 60, 3), where each value in the height and width represents a pixel of the image, and the depth represents the R, G, B color values of the image. 

![](/images/album_example.png) ![](/images/album_example2.png) ![](/images/album_example3.png) 

Convolutional Neural Networks (CNN's) were chosen for this Image Classification Regression analysis. CNN layers are able to reduce the high dimensionality of images without losing its information, which will allow the computer to "view" each image at a hollistic level.

The first model run kept the initial dimensions of Spotify album artwork, (664, 664, 3). with one CNN layer and Pooling layer. This model did not perform well, as it used too much computational power. 

After resizing photos to (60, 60, 3) the models ran much faster. The remaining models tested involved adding / removing layers, increasing epochs, and tuning hyperparameters to find the lowest MSE score. The final model chosen generated an MSE of 144.9, with a filter size of 5 x 5, a pooling size of 2 x 2, linear activation, and no padding. Although this model outperformed the others, it is not an effective predictor for Spotify's popularity index. The scatterplot of true vs. predicted values demonstrate this, as well as it's R Squared score of 0. This score essentially tells us the model is about as efficient at predicting popularity than a simple averaging of popularity, 30.7, would be able to predict.

Epoch by Mean Squared Error | Scatterplot of True Vs. Predicted Values |
--- | --- |
![](/images/line_chart.png)  | ![](/images/scatterplot.png)  | 

# Conclusion

Due to the model's MSE and R Squared score, it is evident this model has poor predicitve ability and should not be used to gauge an track's popularity on Spotify. A lack of predictability could serve as an insight in itself however, as it is highly possible that users no longer focus on album artwork. 

With more time I would attempt to support the above theory by running the same analysis on albums from the 80's up to the early 2000's. I would also look into finding a different target variable to measure "success". Spotify's metric is based on recency, which therefore overlooks older music. It also rates popularity comparatively to other songs, which is problem a because songs that may be popular within their own genre could be understated due to the popularity of other genres. Lastly, I would run a NLP analysis on track name, and see if this has any effect on popularity among Spotify listeners. 

# Repository Navigation


## Reproduction Instructions

To gather the same results as what's detailed in this .README, simply run the final_model.ipynb notebook. This will read in the data saved in this GitHub.

If the user would like to rerun this analysis with the most current Spotify playlists, The user needs to create a developer account and gain credentials for Spotify's API. Details are linked [here.](https://spotipy.readthedocs.io/en/master/#getting-started) Once the user has a CID and Secret key, those should be pasted in the third cell of Spotify_API_pull.ipynb. This notebook can then be run, and the new album artwork and popularity indices will be saved. The user can then run final_model.ipynb to generate CNN models. 

## Repository Structure

```
├── data : data used for modeling, includes album art and popularity index pulled from Spotify API
├── images : images used in PPT and README
├── README.md : project information and repository structure
├── .pptx : Presentation for Stakeholders
└── .ipynb : Jupyter notebook used for modeling
```
