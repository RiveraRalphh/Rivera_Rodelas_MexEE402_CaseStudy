# MexEE 402: Data Preprocessing Case Study

MexEE Elective 2: Data Science and Machine Learning
Batangas State University, Alangilan Campus
1st Semester, AY 2026-2027

## Members

| Name | Student Number | Section |
|---|---|---|
| Rivera, Ralph | 22-06648 | Mexe-4103 |
| Rodelas, Desmond | 22-01230 | Mexe-4103 |

## Notebook links

| Chapter | Member 1 | Member 2 |
|---|---|---|
| Ch1_2_3 | [link]() | https://colab.research.google.com/drive/1t3TEiNXIex-QNjkZloTiIKsfjYvBY7-Z?usp=sharing |
| Ch4 | [link]() | [link]() |
| Ch5 | [link]() | [link]() |
| Ch6 | https://colab.research.google.com/drive/1iDh6p4fBVhIIbyh20GOidgWpHkIkYYlH?usp=sharing | [link]() |
| Ch7 | https://colab.research.google.com/drive/1aPI1P-aj537JwyzoVb80XNlNyqSEq1zo?usp=sharing | [link]() |
| Ch8 | https://colab.research.google.com/drive/190w0Ar96hQ2fP-j1ny48yFikYhEw4t84?usp=sharing | [link]() |
| Ch9 | https://colab.research.google.com/drive/16lSYkT5KT5QoipT-Mi15y78mpmrBuF4b?usp=sharing | [link]() |

## What we learned

### Chapter 6 : Dealing with Outliers

I understood that real-world datasets are rarely model-ready and require tailored handling of missing values rather than simple deletion. Using strategies such as median imputation for numerical features like Age and Fare and constant fills for categorical features reduces massive data loss while maintaining feature integrity. What surprised me was the volume of missing data, particularly in Cabin, and how dropping rows arbitrarily can severely bias a model when compared to imputing.

### Chapter 7 : Feature Selection

I learned how raw continuous and categorical attributes must be converted into numerical representations that machine learning algorithms can mathematically process. OneHotEncoder transforms different categorical labels such as Sex, Embarked, and Pclass, into binary indicator columns, while Standard Scaler standardizes numerical variables to prevent features with wider ranges from dominating training. The fact that categorical features, such as Pclass, frequently perform better when encoded categorically as opposed to being treated as straightforward numerical scales surprised me because it eliminates implicit distance assumptions.

### Chapter 8 : Constructing a Preprocessing Pipeline

I learned that non-linear relationships that a typical continuous model might overlook can be highlighted by classifying continuous variables into discrete bins like converting continuous Age values into Child, Adult, and Elderly categories. Additionally, dropping non-informative columns like Passenger Id, Name, and Ticket reduces noise and dimensional complexity. I was surprised by how much domain-specific feature engineering (like life-stage binning) can simplify data variance without sacrificing predictive clarity.

### Chapter 9 : Real-World Application: Data Preprocessing

I learned how to tie independent preprocessing steps like imputation, scaling, and encoding into a unified workflow using Column Transformer to prevent data leakage and streamline multi-step modeling. Evaluating the final transformed dataset verified that missing values across all features were completely eliminated (reduced to 0). What surprised me was how concise and reusable a well-constructed pipeline makes the data transformation process compared to manually applying separate transformers to individual DataFrames.

## Errors we found

One of the main issues found in the original notebooks was how missing categorical data was handled. Numerical imputation methods, such as using the mean or median, were mistakenly applied to string-based columns. This resulted in execution errors and incorrect data types. To fix this, SimpleImputer was configured with strategy='constant' and fill_value='missing' specifically for categorical variables.

Another important issue was data leakage during feature scaling. In the original version, tools like StandardScaler were fitted using the entire dataset before it was split into training and testing sets. This meant that information from the test or validation data could unintentionally influence the training process. The corrected version prevents this by fitting the scalers only on the training data through a ColumnTransformer pipeline.

Lastly, categorical variables such as Embarked were initially converted into numerical values using label encoding. This created an unintended order between the categories, as if values like S, C, and Q had a mathematical relationship. To avoid this, OneHotEncoder(handle_unknown='ignore') was used instead. This converts each category into its own binary column without implying any ranking or order between them.

## Note on AI tools

We used an AI tool like GeminiAI to assist with analyzing code structure, summarizing dataset pipelines, checking preprocessing steps, and formatting reflections clearly based on the notebook outputs.

## References

McKinney, W. (2021). Python for Data Analysis, 3rd ed. O'Reilly.
VanderPlas, J. Python Data Science Handbook.
Any other page or article you used.
