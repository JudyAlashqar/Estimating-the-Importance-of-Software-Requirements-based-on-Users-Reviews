# Estimating-the-Importance-of-Software-Requirements-based-on-Users-Reviews
Python Project to Analyze User's Reviews on Software Applications and Extract Information from them that are Useful for the Development in the Next Sprints.
### After Collecting Users' Reviews on a Software Application and Software Requirements for this Application, the Proposed Approach Consists of 7 main Practical Stages:
* Representing Users' Reviews using multiple Syntactical and Semantic Representations.
* Build and Train Machine Learning Models to Filter these Reviews (Classify them to: Contains a Requirement/ Does Not Contain a Requirement).
* Build and Train Machine Learning Models to Classify these Reviews to: Feature Request/ Bug Report/ Information Sharing.
* Using a Pretrained Model to identify the Sentiment for each Review.
* Matching each Review with the Requirement(s) it Mentions.
* Estimating the Importance (Priority) of the Mentioned Requirements according to three indicators: Mentions Ratio among Reviews, Requirement Type (Feature Request, Bug Report, Information Sharing), Requirement Sentiment; where second and third indicators are defined based on the reviews that mentioned this requirement.
* Clustering the Reviews that did not match with any requirement, and extract Keywords from each Cluster to provide Suggestions for new Requirements.
### Implementation
There are three uploaded Jupyter Notebooks to Implement the Stages deomonstrated above. We will explain which Stages are Implemented in each of them, Text Representation Methods and ML Models used, Datasets used, in addition to the Results.
#### First: Reviews Filtering and Classificaion.ipynb
The Provided Python Code in this Notebook can be Used to Filter Reviews (Classify them to: Contains a Requirement/ Does Not Contain a Requirement), in addition to Classify these Reviews to: Feature Request/ Bug Report/ Information Sharing.
##### Datasets:
* [Maalej Dataset.xlsx](https://github.com/JudyAlashqar/Estimating-the-Importance-of-Software-Requirements-based-on-Users-Reviews/files/13050211/Maalej.Dataset.xlsx)

