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

# SteamVox v0.1 features
1. Scrapes reviews for your chosen game (Credit to https://github.com/woctezuma/download-steam-reviews! Thanks so much for all those discussions and upgrades.)
2. Cleans unhelpful reviews out of the dataset
3. Breaks usable reviews into paragraphs, then assigns topics (game features) and sentiment scores
4. Provides snapshot of player sentiment per game feature
5. Model identifies topics correctly ~85% of the time 


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
