**Personality Prediction from Text**
-
**Assignment Overview**
-
This assignment aims to predict Myers-Briggs Type Indicator (MBTI) personality traits from text data. Using natural language processing techniques and machine learning algorithms, the system analyzes written text to classify individuals across the four MBTI dimensions:

1. **Mind**: Introversion (I) vs. Extraversion (E)
2. **Energy**: Intuition (N) vs. Sensing (S)
3. **Nature**: Feeling (F) vs. Thinking (T)
4. **Tactics**: Perceiving (P) vs. Judging (J)


The model can predict a complete 4-letter MBTI type (e.g., INTJ, ENFP) based on a sample of written text, providing insights into personality traits from language use patterns.


**Dataset**
-
The assignment uses the **MBTI Dataset**, which contains:

• Text samples (posts) from individuals

• Corresponding MBTI personality types

• Each entry includes multiple posts from a person labeled with their self-reported MBTI type


The dataset shows significant class imbalance across the 16 MBTI types, with certain types (particularly those including "N" - Intuition) being overrepresented. This imbalance is addressed in the modeling approach.

**Content**
This dataset contains over 8600 rows of data, on each row is a person’s:

- Type (This persons 4 letter MBTI code/type)
- A section of each of the last 50 things they have posted (Each entry separated by "|||" (3 pipe characters))

**Source**:
https://www.kaggle.com/datasets/datasnaek/MBTI-type/data

**Methodology**
-
**Text Preprocessing**
-
Raw text data undergoes a comprehensive cleaning pipeline:

1. **URL Removal**: Eliminates web links that don't contribute to personality analysis
2. **Special Character Removal**: Keeps only letters and spaces
3. **Lowercase Conversion**: Standardizes all text
4. **Tokenization**: Splits text into individual words
5. **Stopword Removal**: Filters out common English words (e.g., 'the', 'a', 'is')
6. **Lemmatization**: Reduces words to their root form (e.g., 'walking' \u2192 'walk')


**Feature Extraction**
-
The cleaned text is transformed into numerical features using:

• **TF-IDF Vectorization**: Converts text into a matrix where each row represents a document and each column represents a term

• **N-gram Range**: Includes both unigrams and bigrams (1-2 word combinations)

• **Vocabulary Limitation**: Restricts to the 5,000 most frequent terms to manage dimensionality


**Modeling Approach**
-
The assignment uses a divide-and-conquer approach:

1. **Separate Binary Classifiers**: Instead of predicting all 16 MBTI types at once, four separate binary classifiers are trained - one for each MBTI dimension
2. **Model Selection**: Logistic Regression with balanced class weights to handle class imbalance
3. **Training Strategy**: Each model is trained on the same text features but predicts a different binary outcome:
- I/E (Introversion vs. Extraversion)
- N/S (Intuition vs. Sensing)
- F/T (Feeling vs. Thinking)
- P/J (Perceiving vs. Judging)


**Results**
-
The models achieved the following performance metrics:


**Mind:** Introversion (I) vs. Extraversion (E)

• **Accuracy**: 84.4%

• **F1-Score**: 0.90 for Introversion, 0.68 for Extraversion


**Energy:** Intuition (N) vs. Sensing (S)

• **Accuracy**: 88%

• **F1-Score**: 0.93 for Intuition, 0.65 for Sensing


**Nature:** Feeling (F) vs. Thinking (T)

• **Accuracy**: 85%

• **F1-Score**: 0.86 for Feeling, 0.84 for Thinking


**Tactics:** Perceiving (P) vs. Judging (J)

• **Accuracy**: 80%

• **F1-Score**: 0.84 for Perceiving, 0.75 for Judging


The combined model successfully predicts complete MBTI types from text samples, as demonstrated with test cases that correctly identified:

• An empathetic, community-focused text as ENTJ

• A structured, responsibility-oriented text as ISTJ


**Key Insights**
-
1. **Class Imbalance Impact**: The models perform better on majority classes, particularly for the N/S dimension where intuitive types are overrepresented in the dataset
2. **Dimension Difficulty**: The P/J dimension appears to be the most challenging to predict accurately
3. **Balanced Performance**: The F/T dimension shows the most balanced performance between classes
4. **Text Indicators**: Certain language patterns and word choices appear strongly correlated with specific personality traits


**Applications**
-
This personality prediction system could be applied to:

• Personalized content recommendations

• Team composition and dynamics analysis

• Customer service personalization

• Career guidance based on communication style

• Enhanced user experience in digital products


**Limitations**
-
• Relies on self-reported MBTI types which may not always be accurate

• Dataset imbalance affects model performance for underrepresented types

• Text-based prediction captures only the linguistic aspects of personality

• Cultural and linguistic variations may affect prediction accuracy
