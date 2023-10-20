# Estimating-the-Importance-of-Software-Requirements-based-on-Users-Reviews
Python Project to Analyze User's Reviews on Software Applications and Extract Information from them that are Useful for the Development in the Next Sprints.
## After Collecting Users' Reviews on a Software Application and Software Requirements for this Application, the Proposed Approach Consists of 7 main Practical Stages:
* Representing Users' Reviews using multiple Syntactical and Semantic Representations.
* Build and Train Machine Learning Models to Filter these Reviews (Classify them to: Contains a Requirement/ Does Not Contain a Requirement).
* Build and Train Machine Learning Models to Classify these Reviews to: Feature Request/ Bug Report/ Information Sharing.
* Using a Pretrained Model to identify the Sentiment for each Review.
* Matching each Review with the Requirement(s) it Mentions.
* Estimating the Importance (Priority) of the Mentioned Requirements according to three indicators: Mentions Ratio among Reviews, Requirement Type (Feature Request, Bug Report, Information Sharing), Requirement Sentiment; where second and third indicators are defined based on the reviews that mentioned this requirement.
* Clustering the Reviews that did not match with any requirement, and extract Keywords from each Cluster to provide Suggestions for new Requirements.
## Implementation
There are three uploaded Jupyter Notebooks to Implement the Stages deomonstrated above. We will explain which Stages are Implemented in each of them, Text Representation Methods and ML Models used, Datasets used, in addition to the Results.
### First: Reviews Filtering and Classificaion.ipynb
The Provided Python Code in this Notebook can be Used to Filter Reviews (Classify them to: Contains a Requirement/ Does Not Contain a Requirement), in addition to Classify these Reviews to: Feature Request/ Bug Report/ Information Sharing.
#### Filtering Datasets:
* [Maalej Filtering ‏Dataset.txt](https://github.com/JudyAlashqar/Estimating-the-Importance-of-Software-Requirements-based-on-Users-Reviews/files/13050297/Maalej.Filtering.Dataset.txt)
[Alshangiti, Moayad, et al. "Hierarchical bayesian multi-kernel learning for integrated
classification and summarization of app reviews." Proceedings of the 30th ACM Joint European
Software Engineering Conference and Symposium on the Foundations of Software Engineering.
2022]
* [P1-Golden.xlsx](https://github.com/JudyAlashqar/Estimating-the-Importance-of-Software-Requirements-based-on-Users-Reviews/files/13050303/P1-Golden.xlsx)
[Mekala, Rohan Reddy, et al. "Classifying user requirements from online feedback in small
dataset environments using deep learning." 2021 IEEE 29th International requirements
engineering conference (RE). IEEE, 2021]
#### Classification to Types Datasets:
* [Maalej Dataset.xlsx](https://github.com/JudyAlashqar/Estimating-the-Importance-of-Software-Requirements-based-on-Users-Reviews/files/13050211/Maalej.Dataset.xlsx)
* [Pan Dataset.xlsx](https://github.com/JudyAlashqar/Estimating-the-Importance-of-Software-Requirements-based-on-Users-Reviews/files/13050252/Pan.Dataset.xlsx)\
[Al-hawari, assem (2019), “A dataset of Mobile application reviews for classifying reviews
into software Engineering's maintenance tasks using data mining techniques”, Mendeley Data, V2,
doi: 10.17632/5fk732vkwr.2]
#### Text Representaion Methods:
* BOW (Binary, TF, TF-IDF).
* Embedding (FastText pretrained on Domain, Facebook pretrained FastText, Bert CLS Token, Fine-tuned BERT).\
  Used Fast Text Pretrained on Domain: https://drive.google.com/file/d/1JFrGM43Jq8W2tanKBReu2jLNqN5uPoea/view [Alshangiti, Moayad, et al. "Hierarchical bayesian multi-kernel learning for integrated
classification and summarization of app reviews." Proceedings of the 30th ACM Joint European
Software Engineering Conference and Symposium on the Foundations of Software Engineering.
2022]
#### Machine Learning Models:
* Support Vector Machine.
* Neural Network with One Fully-Connected Layer.
#### Results:
* Filtering Stage: Best Model is FastText Pretrained on Domain + Neural Network. The Model achieved F1-Score equals to 88% on P1-Golden dataset, 78% on Maleej Filtering dataset, and 80% on the Union of the two datasets.\
  Reviews Filtering Model: https://drive.google.com/drive/folders/1dyR73Q6d4ZPDQ2VAECFaQ0xtB5Kj8xQz?usp=share_link \
* Classification Stage: Best Model is FastText Pretrained on Domain + Neural Network. The Model achieved F1-Score equals to 66% on Maleej dataset, 74% on Pan dataset, and 74% on the Union of the two datasets (removing rating class, in addition to merging information seeking, information giving, and user experience under one class).\
  Reviews Classification Model: https://drive.google.com/drive/folders/1QfP23TS302D-lAew_PHMDn403nc-v-JI?usp=share_link
### Second: Review-Requirement Matching.ipynb


