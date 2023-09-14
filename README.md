
# A complete Introduction

  In an era defined by the ever-increasing volume of data generated daily, the field of machine learning stands at the forefront of transforming this data deluge into actionable insights. This project embarks on a journey into the realm of machine learning, with a focus on predicting the popularity of songs. The fascination with music is a universal language that transcends borders, cultures, and generations. Understanding what makes a song popular has long been a subject of intrigue and curiosity.
# A completed write that includes the following
A. Introduction of your project. Why chosen? why is it cool? General/Broader impact of having a good predictive mode. i.e. why is this important?

- The choice of predicting song popularity stems from a profound interest in the intersection of data science and the arts. Music, a form of artistic expression, can often defy conventional analysis due to its subjective nature. However, the power of data and machine learning offers an opportunity to decipher some of the underlying patterns that contribute to a song's popularity. By undertaking this project, we aim to unravel the intricate web of features and factors that influence a song's reception by its audience.
    
- The coolness factor of this project lies in its ability to merge the worlds of data science and music appreciation. It allows us to delve into the very essence of what makes a song resonate with listeners. Moreover, by breaking down the components of a song, from its instrumental qualities to its lyrical content, we can gain insights that are not only intriguing but also potentially valuable for artists, music producers, and the music industry at large. Additionally, the challenge of converting a regression problem into a classification task by categorizing song popularity adds an interesting twist to the project.
    
- The broader impact of building a good predictive model for song popularity extends beyond mere entertainment. The music industry, with its immense economic and cultural significance, can greatly benefit from such predictive models. Artists and producers can make informed decisions about songwriting, production, and marketing strategies. Music streaming platforms can enhance user recommendations, leading to more personalized and enjoyable music experiences for their listeners. This project offers a glimpse into the potential for data-driven decision-making within the creative domain, highlighting the broader implications of machine learning in various industries.


B. Methods section (this section will include the exploration results, preprocessing steps, models chosen in the order they were executed. Parameters chosen. Please make sub-sections for every step. i.e Data Exploration, Preprocessing, Model 1, Model 2, (note models can be the same i.e. CNN but different versions of it if they are distinct enough). You can put links here to notebooks and/or code blocks using three ` in markup for displaying code. so it would look like this: ``` MY CODE BLOCK ```
Note: A methods section does not include any why. the reason why will be in the discussion section. This is just a summary of your methods.

# Methods
 # 1. Data Exploration
In this initial phase, we conducted an in-depth exploration of the dataset to gain insights into its characteristics and identify potential challenges. Key steps and findings include:
-  Missing Data Analysis: We calculated the proportion of missing data for each column and identified columns with significant missing values. This helped us decide which columns to drop or retain.
```
# Missing Data Analysis
missing_proportion = df.isnull().sum() / len(df)
missing_proportion = missing_proportion[missing_proportion > 0]
```
- Categorical Column Analysis: We examined categorical columns to understand the unique values they contained. This exploration informed our decision to drop columns with an excessive number of unique categories.
```
# Categorical Column Analysis
categorical_columns = df_droppedna.select_dtypes(include=['object']).columns
unique_counts = df_droppedna[categorical_columns].nunique()
```

# 2. Data Preprocessing
After gaining insights from data exploration, we performed several preprocessing steps to prepare the data for modeling:
Handling Missing Data: We dropped columns with a high proportion of missing data and removed rows with missing values in other columns.
- Handling Missing Data
df_droppedna = df.dropna(subset=columns_to_check).drop(['Track Preview URL', "Album Genres"], axis=1)

Handling Categorical Data: We encoded categorical columns using Label Encoding to convert them into a numeric format suitable for machine learning models.
```
# Encoding Categorical Data
for col in categorical_cols:
le = LabelEncoder()
df_encoded[col] = le.fit_transform(df_encoded[col])
```

# 3. Model Selection
For this project, we chose two initial machine learning models to predict song popularity:
Random Forest Classifier: We employed the Random Forest classifier for its ability to handle complex relationships in data and provide feature importance rankings.
Decision Tree Classifier: In addition to Random Forest, we also trained a Decision Tree classifier, which served as a baseline model for comparison.
Support Vector Machine: We explored the application of Support Vector Machines (SVM) on our dataset, leveraging both the preprocessed and encoded data from our initial Random Forest Model. While SVM is a powerful supervised learning method, the results, unfortunately, did not meet our initial expectations. 
# 4. Model Training and Evaluation
We split the data into training and testing sets and trained both models on the training data. Subsequently, we evaluated their performance using accuracy as the metric.
```
# Model Training and Evaluation
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3)
rf = RandomForestClassifier()
dt = DecisionTreeClassifier()
rf.fit(X_train, y_train)
dt.fit(X_train, y_train)
rf_predictions = rf.predict(X_test)
dt_predictions = dt.predict(X_test)
rf_accuracy = accuracy_score(y_test, rf_predictions)
dt_accuracy = accuracy_score(y_test, dt_predictions)
```
# 5. Hyperparameter Tuning
To optimize the performance of the Random Forest model, we conducted hyperparameter tuning using GridSearchCV. This involved searching for the best combination of hyperparameters, including the number of estimators, maximum depth, minimum samples split, and minimum samples leaf.
```
# Hyperparameter Tuning
param_grid = {
    'n_estimators': [10, 50, 100, 200],
    'max_depth': [None, 10, 20, 30],
    'min_samples_split': [2, 5, 10],
    'min_samples_leaf': [1, 2, 4]
}
grid_search = GridSearchCV(RandomForestClassifier(random_state=42), param_grid, cv=5, verbose=1, n_jobs=-1)
grid_search.fit(X_train, y_train)
best_rf = grid_search.best_estimator_
```
This structured Methods section provides a concise summary of the steps involved in your project, from data exploration and preprocessing to model selection and hyperparameter tuning. For more detailed information and code blocks, please refer to the corresponding notebooks or code files.

**C. Results section:** 

This will include the results from the methods listed above (C). You will have figures here about your results as well.
No exploration of results is done here. This is mainly just a summary of your results. The sub-sections will be the same as the sections in your methods section.

- 1. ![74e9f4f0-660e-445b-a35c-6950b280910c](https://github.com/ItsBaiShiXi/MachineLearning_SongPopularity/assets/134015247/86b0b083-8f2b-4471-baaa-f92543cdb9cb)

- 2. ![f976605e-e258-48fd-a726-5e701705a66c](https://github.com/ItsBaiShiXi/MachineLearning_SongPopularity/assets/134015247/a89c6ca4-c51c-4c89-b1c3-14b7776dbd48)

- 3. ![88b9c6e0-2e25-42ec-8083-be9beb4d6dd8](https://github.com/ItsBaiShiXi/MachineLearning_SongPopularity/assets/134015247/27842063-8e4a-44a0-8359-976fec1aa585)

- 4. ![2cce643c-acce-43f6-b6d4-b6fd1a2b4c0f](https://github.com/ItsBaiShiXi/MachineLearning_SongPopularity/assets/134015247/ab5d8f3a-e841-49c4-be7d-ef9f7c65fe82)

  
**D. Discussion section:** This is where you will discuss the why, and your interpretation and your thought process from beginning to end. This will mimic the sections you have created in your methods section as well as new sections you feel you need to create. You can also discuss how believable your results are at each step. You can discuss any shortcomings. It's ok to criticize as this shows your intellectual merit, as to how you are thinking about things scientifically and how you are able to correctly scrutinize things and find shortcomings. In science we never really find the perfect solution, especially since we know something will probably come up in the future (i.e. donkeys) and mess everything up. If you do it's probably a unicorn or the data and model you chose are just perfect for each other!

**A) 1. Data Exploration**
During the data exploration phase, we observed several key aspects of the dataset. One notable finding was the presence of missing data in some columns, particularly in the 'Album Genres' and 'Track Preview URL' columns. We decided to drop 'Album Genres' due to its complete absence of data, while for 'Track Preview URL,' we retained the column but dropped rows with missing values.

**B) 2. Data Preprocessing**
We applied the necessary preprocessing steps to prepare the data for modeling. Encoding categorical data was essential to ensure compatibility with machine learning algorithms. The decision to categorize song popularity into five classes was made based on the widely distributed nature of the 'Popularity' column. This categorization transformed our regression problem into a classification task.

**C) 3. Model Selection and Training**
We selected two classification models, Random Forest, and Decision Tree, as our initial candidates for predicting song popularity. Both models were trained on the preprocessed data, and their accuracy on the test dataset was evaluated.

**D) Hyperparameter Tuning**
Hyperparameter tuning was conducted on the Random Forest model to find the best combination of hyperparameters. The selected parameters, including the number of estimators, maximum depth, minimum samples split, and minimum samples leaf, aimed to optimize the model's performance.

**E. 5) Believability of Results**

**1.** The results obtained throughout the project are credible and reliable to a certain extent. However, it's essential to acknowledge the limitations and areas for improvement:

  **a. Data Quality:** The believability of the results heavily relies on the quality of the input data. Any inaccuracies or biases present in the dataset can affect the model's predictions.
Feature Engineering: Our approach to feature engineering was relatively straightforward, primarily involving encoding and categorizing existing features. Future work could explore more sophisticated feature engineering techniques to enhance model performance.

  **b. Model Evaluation:** While accuracy is a valuable metric, it may not be sufficient for assessing model performance comprehensively. Additional evaluation metrics and cross-validation techniques can provide a more nuanced understanding of the models' capabilities.

  **c. Bias and Fairness:** It's crucial to consider potential biases in the dataset, especially when predicting song popularity. Biases related to artist popularity, genre preferences, or time periods may influence the model's predictions.

**Conclusion section:** This is where you do a mind dump on your opinions and possible future directions. Basically what you wish you could have done differently. Here you close with final thoughts

  **A. Opinions and Reflections**
  
  *1:* As we reflect on our project, several key takeaways and opinions come to mind:
    
        a. Intersection of Data Science and Music:* The intersection of data science and music is a rich 
        and promising field. It allows us to combine analytical rigor with artistic expression, 
        offering insights that can benefit artists, producers, and music enthusiasts alike.

        b. Data Quality is Crucial: The quality of the input data is paramount. 
        Inaccuracies, missing values, or biases in the dataset can significantly impact the reliability of our predictive models. 
        Ensuring data integrity is an ongoing challenge.

        c. Model Complexity vs. Interpretability: We encountered the trade-off between model complexity and interpretability. 
        While Random Forest outperformed the Decision Tree, it also introduced greater complexity. 
        Achieving the right balance between accuracy and interpretability is a continuous challenge.
        
  **B. Future Directions**
  
  *1:* Looking ahead, we envision several exciting future directions for this project:
  
      a. Feature Selection: Conduct more thorough feature selection to identify the most influential factors affecting song popularity. 
      This could involve advanced feature selection techniques or domain-specific knowledge.
      
      b. Enhanced Encoding: Experiment with advanced encoding techniques, such as one-hot encoding or target encoding, 
      to capture the nuances of categorical data more effectively.
      
      c. Model Ensemble: Explore ensemble techniques to combine the strengths of multiple models,
      potentially improving predictive accuracy.
      
      d. Fairness and Bias Analysis: Dive deeper into fairness and bias analysis to ensure that our model's predictions are equitable
      and not influenced by demographic or genre-related factors.
      
      e. User Engagement Metrics: Expand the scope by incorporating user engagement metrics, such as user reviews and streaming counts, 
      to enhance prediction accuracy and provide a more holistic view of song popularity
      
      
**C. Final Thoughts**

  **1:** In conclusion, this project represents the beginning of an exciting journey into the realms of music and data science. While we have made valuable strides in predicting song popularity, there is still much ground to cover. We anticipate that the fusion of data-driven insights with the creative domain of music will continue to yield exciting discoveries and innovations.
  
  **2:** Our project serves as a testament to the potential of data science to unravel the mysteries of art and culture. As we close this chapter, we are left with a deep appreciation for the power of data and the limitless possibilities it offers in understanding and enhancing the world of music.
  
  **3:** As we bid farewell to this project, we look forward to the harmonious symphony of data and creativity that awaits in future endeavors, each note bringing us closer to unlocking the secrets of our ever-evolving musical landscape.
  

**F. Collaboration section:** This is a statement of contribution by each member. This will be taken into consideration when making the final grade for each member in the group. Did you work as a team? was there a team leader? project manager? coding? writer? etc. Please be truthful about this as this will determine individual grades in participation. There is no job that is better than the other. If you did no code but did the entire write up and gave feedback during the steps and collaborated then you would still get full credit. If you only coded but gave feedback on the write up and other things, then you still get full credit. If you managed everyone and the deadlines and setup meetings and communicated with teaching staff only then you get full credit. Every role is important as long as you collaborated and were integral to the completion of the project. If the person did nothing. they risk getting a big fat 0. Just like in any job, if you did nothing, you have the risk of getting fired. Teamwork is one of the most important qualities in industry and academia!!!
Start with Name: Title: Contribution. If the person contributed nothing then just put in writing: Did not participate in the project.

*Devansh Vora:*
- Wrote this entire readme file
- Wrote most of the readme file for the previous submission
- Collaborated in modeling for the first time

*ShengZhe Zhang:*
- Communicate with each group member and assign their role in the project
- Finished the first version of data preprocessing
- Finished the first version of Random Forest Model and ReadMe

*Krithik Parvataneni:*
- Worked on the first version of the model(Decision Tree/SVM Model) with Lisa
- Wrote initial Part of ReadMe
  
*Lisa Verma:*
- Collaborated with Krithik on the first version of the model(Decision Tree/SVM Model)
- Wrote initial Part of ReadMe
  
*Huanlong Li:*
- Collaborated with ShengZhe with first version of Random Forest Model
- Worked on second version of Random Forest Model
  
*Yushen Zheng:*
- Collaborated with ShengZhe and Huanlong on first version of Random Forest Model
- Work on the first version of ReadMe
- Worked on the first version of Decision Tree/ SVM ReadMe
- Fix on Final version of ReadMe
