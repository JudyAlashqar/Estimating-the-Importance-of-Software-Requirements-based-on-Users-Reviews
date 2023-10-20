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
  Reviews Filtering Model: https://drive.google.com/drive/folders/1dyR73Q6d4ZPDQ2VAECFaQ0xtB5Kj8xQz?usp=share_link
* Classification Stage: Best Model is FastText Pretrained on Domain + Neural Network. The Model achieved F1-Score equals to 66% on Maleej dataset, 74% on Pan dataset, and 74% on the Union of the two datasets (removing rating class, in addition to merging information seeking, information giving, and user experience under one class).\
  Reviews Classification Model: https://drive.google.com/drive/folders/1QfP23TS302D-lAew_PHMDn403nc-v-JI?usp=share_link
### Second: Review-Requirement Matching.ipynb
The Provided Code in this Notebook used to determine the suitable Threshold to Match each Review with the Requirement(s) it talks about.
#### Datasets:
* 100 Reviews on Facebook Messenger Application [Jha, Nishant, and Anas Mahmoud. "Using frame semantics for classifying and summarizing
application store reviews." Empirical Software Engineering 23 (2018): 3734-3767]
* 70 Software Requirement for Facebook Messenger Application written in user-story template, Collected using OpenAI ChatGPT [Messenger_requirements.txt](https://github.com/JudyAlashqar/Estimating-the-Importance-of-Software-Requirements-based-on-Users-Reviews/files/13051418/_Messenger_requirements.txt)
* Review-Requirements Matching Dataset Annotated Manually by the Code Author Only [Messenger Facebook Requirement-Review Matching.txt](https://github.com/JudyAlashqar/Estimating-the-Importance-of-Software-Requirements-based-on-Users-Reviews/files/13051068/Messenger.Facebook.Requirement-Review.Matching.txt)
#### Text Representation Methods:
* Pretrained FastText on Domain: https://drive.google.com/file/d/1JFrGM43Jq8W2tanKBReu2jLNqN5uPoea/view [Alshangiti, Moayad, et al. "Hierarchical bayesian multi-kernel learning for integrated
classification and summarization of app reviews." Proceedings of the 30th ACM Joint European
Software Engineering Conference and Symposium on the Foundations of Software Engineering.
2022]
#### Apporach:
Cosine Similarity Function. If the Similarity Score between a Review and a Requirement above the specified Threshold, then there is a Match.
#### Results:
After experimenting multiple values, the value 0.75 was adopted for the Similarity Threshold. Using this Value, Recall obtained was 60%, Precision was 30%, and F2-Score was 50%. This Result is considered Acceptable according to the Research Work related to the kind of task we are dealing with [Hayes, Jane Huffman, Alex Dekhtyar, and Senthil Karthikeyan Sundaram. "Advancing
candidate link generation for requirements tracing: The study of methods." IEEE Transactions on
Software Engineering 32.1 (2006): 4-19.]
### Third: Sentiment Analysis_Estimate Requirements Importance_ Suggest New Requirements.ipynb
The Provided Code in this Notebook is used to give a priority score (importance) for each requirement matched with reviews according to the previous stage, and give Keywords that represent suggestions for New Requirements.
#### Approach:
* Sentiment was determined for each Review using Pretrained Model: https://huggingface.co/finiteautomata/bertweet-base-sentiment-analysis
* Type was determined for each Requirement based on the matched reviews with this requirement according to this heuristic:
* * If there is at least One "Bug Report" Review that is related to it, then the Requirement Type is "Bug Report".
  * If there is not any "Bug Report" Reviews but at least One Review that is "Feature Request", then the Requirement Type is "Feature Request".
  * If there is only "Information Sharing" Reviews, then the Requirement Type is "Information Sharing".
* Type Score was determined for each Requirement according to this:
* * If the Requirement Type is "Bug Report", then the Score is 1
  * If the Requirement Type is "Feature Request", then the Score is 0.5
  * If the Requirement Type is "Information Sharing", then the Score is 0.25
* Sentiment Score was determined for each Requirement based on the matched reviews with this requirement according to this heuristic:
#### Results
