# SteamVox

SteamVox is built to obtain the “Voice of the Player” from players’ reviews on Steam (one of the largest online distributors for PC games).

SteamVox scrapes, cleans, and analyses reviews from Steam to identify topics and corresponding sentiment for each topic for a chosen game on Steam.

Using the power of machine learning, it delivers convenient snapshots and narrows down areas of negativity to investigate (and areas of positivity to celebrate!).

Currently only works on Total War: Three Kingdoms. A future iteration will be made applicable across most games on Steam.


# Writeups

Short version can be found [here.](https://medium.com/@tangshuweialfred/steamvox-topic-modelling-sentiment-analysis-d83a88d3003a)

Full technical writeup [here.](https://medium.com/@tangshuweialfred/steamvox-topic-modelling-sentiment-analysis-technical-adc5b88f71a0)


# Etymology

#### Vox Populi, Vox Dei
"The voice of the people is the voice of God."

#### Steam

An [app store for video games](https://store.steampowered.com/) -- the biggest in the world!

# Why SteamVox Matters
When I was a sales optimisation analyst in the video game industry, my team encountered a problem that we were not fully equipped to answer.

Whenever new content was released, product managers wanted to know how players responded to the update. The best we could do without the power of data science was to read a small number of reviews and talk to veteran players to get a rough sense of player sentiment.

There are 2 problems here:

1. This manually gathered data does not necessarily represent the whole player demographic. 
2. Employees can't each spend 20.83 working days reading 10,000 reviews at the rate of 1 per minute with 0 failures. That's a whole month of working hours spent on labelling!
3. By the time you finish compiling the data manually and make a pivot table in Excel, your information could be outdated. 

I made SteamVox to solve precisely this business problem. Instead of spending 21 days reading 10,000 reviews, you could spend 2 hours tweaking settings and training the model, then get your output.

I aim to further develop SteamVox so that it can get you information within minutes, and not just for 1 video game. Stay tuned!


# SteamVox v0.1 features
1. Scrapes reviews for your chosen game (Credit to https://github.com/woctezuma/download-steam-reviews! Thanks so much for all those discussions and upgrades.)
2. Filters out unhelpful reviews
3. Cleans remaining reviews
4. Breaks usable reviews into paragraphs, then assigns topics (game features) and sentiment scores
5. Provides snapshot of player sentiment per game feature
6. Model identifies topics correctly ~85% of the time 
7. Trained on 3600+ usable Steam reviews from Total War: Three Kingdoms (Filtered from 8000+ reviews. Over 100,000 words!)


# More room for improvement

#### Obstacles eliminated
1. Short spam reviews
2. Generic "this is the best game" reviews
3. Typos (filtered out based on frequency)
    - Heavily typoed reviews are relatively uncommon, but not rare (sssooome playersss liek typnggg lkie tissss)
4. Named entities not lost (e.g. characters) - n-grams were helpful
5. Reviews that are long but hold no meaningful tokens

#### Risks minimised, but still present
1. Multiple languages
2. Spam/meme reviews that are very long
3. Misclassification
4. Incorrect sentiment score (related to sarcasm, below)

#### Performance issues
1. Lemmatisation is computationally more intensive and does not work well on large datasets.
    - Stemming will be considered for future optimisation.
    - Some notebooks (especially) this one can take several minutes to run.
    
2. Code may still be heavy to read. 
    - Many cells were converted into more efficient forms (e.g. converting into for loops, functions and function calls)
    - Will explore further optimisation

# References
1. DoctorSnapshot by nuwapi @ https://github.com/nuwapi/DoctorSnapshot/tree/master/src
    - https://blog.insightdatascience.com/topic-modeling-and-sentiment-analysis-to-pinpoint-the-perfect-doctor-6a8fdd4a3904
2. steamreviews scraper by woctezuma @ https://github.com/woctezuma/download-steam-reviews
3. expandContradictions by nealrs @ https://gist.github.com/nealrs/96342d8231b75cf4bb82
4. syntok by fnl @ https://github.com/fnl/syntok
5. Guide to Topic Modelling with Gensim @ https://www.machinelearningplus.com/nlp/topic-modeling-gensim-python/
