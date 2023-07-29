# Identifying YouTube Videos "Made for Kids"

## I. Project Background
In this project, I train models to predict if a YouTube video was "made for kids" or not. The need to identify YouTube videos "made for kids" arose from Federal Trade Commission (FTC) restricting YouTube from collecting user information for childeren under COPPA (Children’s Online Privacy Protection Act). Now, such videos are under certain constraints such as that comments, live chats, notifications, playlists, donations, and other interactive features are turned off on that content. 

YouTube may face legal consequences if content is not categorized correctly. This fact enhances the importance of flagging YouTube videos made for kids. Although users are supposed to label their videos (as seen below), YouTube would want to ensure that this is done in fact correctly.

<img width="363" alt="image" src="https://github.com/suesuyeonlim/naive_bayes_classifier/assets/19903898/af0af2ad-8e02-4219-a642-8b3204f8449c">

## II. YouTube Data API
In predicting the type of YouTube videos, I use video titles, descriptions, and tags. The information can be easily collected using YouTube Data API ([Link](https://developers.google.com/youtube/v3)). I scraped more than 5,000 videos for this project. Below is a scraped data example of a video.
<img width="859" alt="image" src="https://github.com/suesuyeonlim/naive_bayes_classifier/assets/19903898/f1162693-7389-4008-b669-9a11cd441895">

## III. Main Model - Naive Bayes Classifier
There are benefits of using machine learning models in this type of projects. They include the following:
- The models are highly scalable
- They can reduce human efforts of manually reviewing videos
- Consistent criteria are applied in identifying videos made for kids 

Among a wide array of machine learning models, I trained four different models: 1) Gradient Boosting; 2) AdaBoost; 3) Naive Bayes; and 4) XGBoost. Among them, Naive Bayes works the best among the four models for this project. In general, Naive Bayes classifier works well for text classification. It calculates the distribution of words showing up for each class (e.g., videos "made for kids" or "not made for kids"), and derives probabilities of having the words that a video has under each class. Finally, it picks the class with a higher probability as the predicted class for the video.

![image](https://github.com/suesuyeonlim/naive_bayes_classifier/assets/19903898/0e79372c-1885-4279-97d6-f9493e89a025)


## IV. Training & Result
For training purposes, I use 75% of the collected videos. I reserve 25% of the videos for testing the accuracy of different models. Also, I use grid search to explore different parameters and find the best ones.

By using Naive Bayes classifier, 92% of videos “made for kids” are identified accurately based on the validation data. Additionally, 98% of videos “not made for kids” are not flagged. It is crucial to consider not only the "made for kids" videos identified correctly, but also the "not made for kids" videos not wrongly concluded as "made for kids". This is because we do not want to find too many false positives and make them subject to the aforementioned constraints.

## V. Next Steps
- Include more videos for training, especially the videos made for kids. At the moment, the models appear to train better or worse depending on the sample it draws from the majority class as only the same number of videos as the ones made for kids can be sampled.
- Try different kinds of parameters to improve the models. Besides alphas and learning rates, there are other parameters such as base estimators, max depths, etc. Tuning such parameters can potentially improve the models.
- Try different data set-ups to improve the models. Some models may work better even with slightly imbalanced data, which allows using more data from the majority class. Also, for Naive Bayes models, it may potentially make sense to remove correlated words to comply with the assumption of independence.

## VI. Locations of Data/Analysis
Data: See "Data" folder.
Analysis: See "Code.ipynb".
Analysis Summary: See "Project 3 Presentation.pdf".
