# SteamVox
SteamVox (WIP) is a tool for getting snapshots of what players are saying about your video game! 

As of Jul/Aug 2019, this tool is for Total War: Three Kingdoms only, as a proof of concept... but stay tuned for more updates!

I intend to make this tool generally applicable across Steam games.

# Etymology

#### Vox Populi, Vox Dei
The voice of the people is the voice of God.

#### Steam

An (app store for video games)[https://store.steampowered.com/] -- the biggest in the world!

#### Vox
noun
noun: vox; plural noun: voxes
(especially in music journalism) vocals; voice.
"his matinee-idol vox"
(Credit to Google-sensei for this definition)

# Why SteamVox Matters
When I was in a sales optimisation role in the video game industry, my team encountered a problem that we were not equipped to answer.

Whenever new content was released, product managers wanted to know how players responded to the update. 

The best we could do without the power of data science was to read a small number of reviews and talk to veteran players to get a rough sense of player sentiment.

The problem is, this manually gathered data does not necessarily represent the whole player demographic. (e.g. 30 opinions can't speak for 1 million people!)

On the other hand, you can't spend 20.83 working days reading 10,000 reviews at the rate of 1 per minute with 0 failures. (Yes, I calculated.) That's a whole month of working hours spent on labelling.

By the time you finish compiling the info manually and make a pivot table in Excel, your information could be outdated. Employees also have better things to do than just sit around reading and labelling Excel cells. 

I made SteamVox to solve precisely this business problem. Instead of spending 21 days reading 10,000 reviews, you could spend 2 hours tweaking settings and training the model, then get your output.

I aim to further build SteamVox so that it can get you information within minutes, and not just for 1 video game. Stay tuned!


# SteamVox v0.1 features
1. Scrapes reviews for your chosen game (Credit to https://github.com/woctezuma/download-steam-reviews! Thanks so much for all those discussions and upgrades.)
2. Cleans unhelpful reviews out of the dataset
3. Breaks usable reviews into paragraphs, then assigns topics (game features) and sentiment scores
4. Provides snapshot of player sentiment per game feature
5. Model identifies topics correctly ~85% of the time 
6. Trained on 3600+ usable Steam reviews from Total War: Three Kingdoms (filtered from 8000+ reviews)
    - Doesn't sound like a lot, does it? But it contains over 100,000 words! (For reference, the New Testament of the Bible contains ~(186,400 words)[https://wordcounter.net/blog/2016/02/21/101241_how-many-pages-are-there-in-the-bible.html])


### More room for improvement

Obstacles eliminated:
1. Short spam reviews
2. Generic "this is the best game" reviews
3. Typos (filtered out based on frequency)
    - Heavily typoed reviews are relatively uncommon, but not rare (sssooome playersss liek typnggg lkie tissss)
4. Named entities not lost (e.g. characters) - n-grams were helpful
5. Reviews that are long but hold no meaningful tokens

Risks minimised, but still present:
1. Multiple languages
2. Spam/meme reviews that are very long
3. Misclassification
4. Incorrect sentiment score (related to sarcasm, below)

Obstacles that the current model cannot handle:
1. Sarcasm
2. Players using vulgarities to emphasise their love for the game (VADER tends to misread these as negatives)
3. Spam reviews that are long and in multiple languages (e.g. players spamming the names of political events in English and Mandarin as a form of online protest against the People's Republic of China)
4. Internet randomness
    - Sometimes, people will write incoherent reviews. 

Performance issues:
1. Lemmatisation is computationally more intensive and does not work well on large datasets.
    - Stemming will be considered for future optimisation.
    - Some notebooks (especially) this one can take several minutes to run.
    
2. Code may still be heavy to read. 
    - Many cells were converted into more efficient forms (e.g. converting into for loops, converting some of those into functions)
    - Will explore further optimisation
