Job Recommendation System Using LinkedIn User Profiles

1. Project Overview

The Job Recommendation System Using LinkedIn User Profiles is a Machine Learning-based web application developed using Python and Django. The main purpose of this project is to help users find suitable job opportunities based on their professional profile, including skills, education, work experience, job preferences, certifications, and other relevant information.

Finding a suitable job manually can be difficult because job portals contain a large number of job postings. A user may have to search through hundreds of jobs and compare the required skills, experience, location, salary, and job descriptions with their own profile.

This project automates this process by analyzing the user's profile and comparing it with available job information. Natural Language Processing (NLP), TF-IDF feature extraction, Random Forest Machine Learning, and cosine similarity are used to identify relevant job opportunities.

The complete application is integrated with a Django web interface. Users can register, log in after administrator activation, provide their professional information, and receive personalized job recommendations.

2. Main Technologies Used

The project uses the following technologies:

* Python - Main programming language
* Django - Web application framework
* HTML/CSS/JavaScript - Frontend interface
* SQLite - Database
* Pandas - Dataset processing
* NumPy - Numerical operations
* Scikit-learn - Machine Learning and NLP
* TF-IDF Vectorizer - Text feature extraction
* Random Forest Classifier - Job-role prediction
* Cosine Similarity - Job matching
* Label Encoder - Encoding job labels
* Matplotlib/Seaborn - Graphs and visualization

The report specifies SQLite as the database and Django as the web framework.

3. Complete Project Execution Flow

The complete execution of the system can be understood as the following flow:


                 START
                   |
                   v
          Open Django Application
                   |
                   v
             User Registration
                   |
                   v
          Admin Verifies User
                   |
                   v
            Account Activated
                   |
                   v
                User Login
                   |
                   v
          Enter Profile Details
                   |
                   v
        Skills + Education + Experience
        + Preferences + Other Details
                   |
                   v
          Load Job Dataset
             (jobs.csv)
                   |
                   v
          Data Preprocessing
                   |
                   v
           Text Processing / NLP
                   |
                   v
             TF-IDF Vectorization
                   |
                   v
          Feature Extraction
                   |
                   v
        Random Forest Model Training
                   |
                   v
        User Profile -> TF-IDF Vector
                   |
                   v
       Random Forest Job Prediction
                   |
                   v
        Compare User with Jobs
                   |
                   v
          Cosine Similarity
                   |
                   v
       Rank Matching Job Opportunities
                   |
                   v
         Select Top Recommendations
                   |
                   v
       Display Recommended Jobs
                   |
                   v
                  END


The report's architecture describes the same basic flow: user profile information is submitted through the Django frontend, TF-IDF converts textual information into numerical vectors, the trained Random Forest model predicts a suitable job, and the recommendation result is returned to the frontend.

4. Step 1: Starting the Django Application

The project is implemented as a Django web application.

When the application is started, Django loads the project configuration, database connection, URLs, models, views, forms, templates, and Machine Learning components.

The user accesses the application through a web browser.

The application provides different interfaces for:

* New user registration
* User login
* User dashboard
* Profile information
* Job recommendation
* Administrator login
* Administrator dashboard
* Dataset management
* Model training
* Results and visualizations

The Django backend handles the communication between the frontend, database, dataset, and Machine Learning model.

5. Step 2: User Registration

The first step for a new user is registration.

The user provides information such as:

* Name
* Email
* Mobile number
* Login ID
* Password
* Professional/profile information

The registration form validates the entered information before saving it.

The submitted information is stored in the Django database.

The project implementation uses a UserRegistrationForm and UserRegistrationModel to process and store registration information.

The user cannot immediately access the complete system because the project uses administrator-based account activation.

6. Step 3: Admin Activation

After registration, the administrator logs into the admin dashboard.

The administrator can:

* View registered users
* View user information
* Activate user accounts
* Deactivate accounts
* Manage datasets
* Monitor training/testing data
* View Machine Learning results

When the administrator activates an account, the user's status changes to an activated state.

Only an activated user is allowed to log in and use the recommendation system.

This provides an additional level of access control.

7. Step 4: User Login

After administrator activation, the user can log in using their credentials.

The login process checks:

1. Login ID
2. Password
3. Account status

If the credentials are valid and the account has been activated, the user is redirected to the user dashboard.

The Django implementation stores session information such as the user ID, username, login ID, and email after successful authentication.

8. Step 5: Creating the User Profile

After login, the user provides the information that will be used for job recommendation.

Important profile information includes:

* Technical skills
* Education
* Work experience
* Certifications
* Projects
* Job title
* Industry
* Job preferences
* Previous ratings/interactions where applicable

For example, a user may enter:

Skills:
Python, Django, Machine Learning, SQL, HTML, CSS

Education:
MCA

Experience:
0 years

Preferences:
Software Developer, Python Developer, Machine Learning


The project uses this information as the main input for the recommendation process.

The report specifically identifies skills, education, work experience, certifications, projects, professional interests, job title, and industry as important profile attributes.

9. Step 6: Loading the Job Dataset

The system requires a job dataset containing available job opportunities.

The project uses a file called:

jobs.csv


The dataset contains job-related information such as:

* Job Title
* Company
* Required Skills
* Location
* Salary
* Job Description
* Apply Link

The administrator can manage the job dataset through the application.

The dataset acts as the source of job information for both Machine Learning and recommendation processing.

10. Step 7: Data Preprocessing

Raw data cannot directly be given to the Machine Learning model.

Therefore, the system first performs data preprocessing.

The preprocessing stage handles:

* Missing values
* Inconsistent data
* Unnecessary information
* Text cleaning
* Categorical information
* Text normalization
* Tokenization
* Stop-word removal

For example, if a job description contains:

We are looking for a Python Developer with experience
in Django and Machine Learning.

The text is processed so that meaningful terms can be represented as Machine Learning features.

The report describes preprocessing of both user profile data and job posting data before Machine Learning processing.

11. Step 8: Combining User Profile Information

The system creates a single text representation of the user's important profile information.

The sample implementation combines:


Skills
Education
Experience
Preferences
Previous Ratings

into a user profile text.

Conceptually, it looks like:

Python Django Machine Learning
MCA
0 years experience
Python Developer Software Developer

This combined text becomes the input for the TF-IDF vectorizer.

The sample code constructs the profile text using the user's skills, education, experience, preferences, and previous ratings.

12. Step 9: TF-IDF Feature Extraction

One of the most important parts of the project is TF-IDF: Term Frequency-Inverse Document Frequency.

TF-IDF converts textual information into numerical vectors that Machine Learning algorithms can process.

The project uses:

TfidfVectorizer(
    stop_words='english',
    ngram_range=(1, 2),
    sublinear_tf=True,
    max_features=500
)


This configuration means:

* English stop words are removed.
* Single words and two-word combinations are considered.
* Important terms receive higher representation.
* The feature set is limited to a maximum of 500 features.

For example, skills such as:

Python
Django
Machine Learning
SQL

are converted into numerical representations.

The same TF-IDF representation is used when processing job-related text so that the user's profile and job information can be compared.

13. Step 10: Feature Extraction

After preprocessing, the system extracts meaningful features from the available information.

The important features include:

Skills
Education
Experience
Certifications
Job Title
Industry
Job Description
Location

These features help the system understand the relationship between a user's profile and available job opportunities.

Feature engineering can also represent information such as:

* Skill similarity
* Experience level
* Job relevance

The purpose of feature extraction is to provide useful numerical information to the Machine Learning model and recommendation process.

14. Step 11: Training the Random Forest Model

The project uses the Random Forest Classifier as the Machine Learning model.

The sample implementation creates the model as:

RandomForestClassifier(
    n_estimators=30,
    max_depth=12,
    random_state=42
)

Here:

* n_estimators=30 means the Random Forest contains 30 decision trees.
* max_depth=12 limits the depth of each tree.
* random_state=42 provides reproducible results.

The model is trained using processed job/profile data.

During training, the model learns patterns between the available features and job roles.

For example:

Python + Django + SQL + MCA
              |
              v
       Python Developer

or:

Machine Learning + Python + Statistics
              |
              v
       ML Engineer / Data Role

The trained model can then predict a suitable job category for a new user profile.

The report identifies Random Forest as the Machine Learning algorithm used for training and prediction.

15. Step 12: Predicting the Suitable Job Role

After the model has been trained, the user's profile is passed through the same TF-IDF vectorizer.

The system creates:

User Profile
     |
     v
TF-IDF Vector
     |
     v
Random Forest Model
     |
     v
Predicted Job Role

The sample implementation uses:

user_vector = tfidf.transform([user_profile_text])

prediction = rf_model.predict(user_vector)

The predicted numerical label is then converted back into the original job title using the Label Encoder.

Therefore, the system can produce a predicted job role based on the user's profile.

16. Step 13: Preparing Jobs for Recommendation

The system does not stop after predicting one job title.

It also searches the available jobs and calculates how closely each job matches the user's profile.

The sample implementation reads up to 5,000 job records:

jobs_df = pd.read_csv('media/jobs.csv', nrows=5000)

For each job, the system combines important information:

Company
Required Skills
Location
Salary
Description

into a single text field called:

combined_features

This gives the system a complete textual representation of each job.

17. Step 14: Converting Jobs into TF-IDF Vectors

The combined job information is passed through the same TF-IDF vectorizer.

The process becomes:

Job Description
      +
Required Skills
      +
Company
      +
Location
      +
Salary
      |
      v
TF-IDF Vectorization
      |
      v
Numerical Job Vector

Now both the user profile and jobs are represented as numerical vectors.

This allows mathematical comparison between the user's profile and every available job.

18. Step 15: Cosine Similarity

The project uses **Cosine Similarity** to determine how closely the user's profile matches each job.

The process is:

User TF-IDF Vector
        |
        |
        v
Cosine Similarity
        ^
        |
        |
Job TF-IDF Vector

A higher similarity score means that the job contains information that is more closely related to the user's profile.

For example:

Python Developer       -> 92%
Django Developer       -> 88%
Data Analyst           -> 76%
Java Developer         -> 41%
Graphic Designer       -> 12%

The jobs are then sorted according to their similarity scores.

The sample code uses cosine_similarity() and sorts the resulting similarity values in descending order.

19. Step 16 – Ranking the Jobs

After calculating similarity scores for the available jobs, the system ranks the jobs from highest similarity to lowest similarity.

For example:

Rank 1 -> Python Developer       92%
Rank 2 -> Django Developer       88%
Rank 3 -> ML Developer           84%
Rank 4 -> Data Analyst           76%
Rank 5 -> Software Developer     73%

This ranking allows the user to see the most relevant opportunities first.

The project report states that recommended jobs are ranked according to relevance and similarity scores.

20. Step 17: Selecting the Final Recommendations

The implementation finally selects the top five recommendations.

Each recommendation contains information such as:

* Job title
* Company
* Required skills
* Location
* Salary
* Description
* Apply link
* Matching score

The sample implementation creates recommendation objects containing these fields and finally selects five jobs.

The output can therefore look like:

1. Python Developer
   Company: ABC Technologies
   Location: Hyderabad
   Skills: Python, Django, SQL
   Match: 92%

2. Django Developer
   Company: XYZ Solutions
   Location: Hyderabad
   Skills: Django, Python, REST API
   Match: 88%

3. Machine Learning Developer
   Company: ABC AI
   Location: Bangalore
   Skills: Python, ML, Pandas
   Match: 84%


21. Step 18: Location-Based Recommendation Handling

The sample implementation contains additional logic for organizing recommendations based on location.

It separates jobs into:

India Jobs
Worldwide Jobs

It also checks specifically for:

Hyderabad Jobs

The implementation attempts to place a suitable Hyderabad job first when matching Hyderabad jobs are available, followed by other India jobs and then worldwide jobs.

This is an implementation-specific behavior present in the sample code.

22. Step 19: Displaying Results in Django

Once the recommendation process is completed, the results are sent back to the Django frontend.

The backend prepares a context containing information such as:

Prediction
Recommended Jobs
User Profile

The frontend then displays the results to the user.

The user can see:

* Predicted job role
* Recommended jobs
* Company names
* Required skills
* Locations
* Salary
* Job descriptions
* Matching percentage
* Apply link where available

This provides a simple interface for the user to understand why particular jobs were recommended.

The report shows separate implementation screens for analyzing the user profile and generating job recommendations.

23. Complete Machine Learning Flow

The Machine Learning portion of the system can be summarized as:


             User Profile
                  |
                  v
        Data Preprocessing
                  |
                  v
          Text Cleaning
                  |
                  v
        TF-IDF Vectorization
                  |
                  v
        Feature Extraction
                  |
                  v
        Random Forest Model
                  |
                  v
        Predicted Job Role
                  |
                  |
                  v
       Compare Against jobs.csv
                  |
                  v
        Job TF-IDF Vectors
                  |
                  v
         Cosine Similarity
                  |
                  v
         Similarity Scores
                  |
                  v
          Sort / Rank Jobs
                  |
                  v
          Select Top 5 Jobs
                  |
                  v
       Display Recommendations


24. Admin Execution Flow

The administrator has a separate workflow:


Admin Login
     |
     v
Admin Dashboard
     |
     +----> View Users
     |
     +----> Activate Users
     |
     +----> Manage Dataset
     |
     +----> Load Training Data
     |
     +----> Train Model
     |
     +----> View Results
     |
     +----> View Performance


The administrator manages users and datasets and can view training/testing information and generated results.

25. Model Evaluation

The project evaluates the Machine Learning model using standard performance metrics:

i. Accuracy
Measures the overall percentage of correct predictions.

ii. Precision

Measures how many of the predicted positive results are actually correct.

iii. Recall

Measures how many of the relevant results are correctly identified.

iv. F1-Score

Provides a combined measure of precision and recall.

The project also provides visualization and analytics for understanding model performance and recommendation behavior.

26. Database Usage

The project uses SQLite as the database.

The database is mainly used for storing application-related information such as:

* User registration details
* Login information
* Account activation status
* User profile information
* Other application records

The database allows the Django application to maintain user information and retrieve it when the recommendation process is executed.

The report specifies SQLite as the project database.

27. Overall System Architecture

The overall architecture can be represented as:

                    USER
                     |
                     v
             Django Frontend
                     |
                     v
              Django Backend
                     |
          +----------+----------+
          |                     |
          v                     v
     SQLite Database        User Profile
                                |
                                v
                       Data Preprocessing
                                |
                                v
                         TF-IDF Vectorizer
                                |
                 +--------------+--------------+
                 |                             |
                 v                             v
          Random Forest                Job Dataset
                 |                     (jobs.csv)
                 |                             |
                 v                             v
          Job Prediction                Job TF-IDF
                                               |
                                               v
                                      Cosine Similarity
                                               |
                                               v
                                      Job Ranking
                                               |
                                               v
                                      Top 5 Jobs
                                               |
                                               v
                                      Django Frontend
                                               |
                                               v
                                            USER

This reflects the client-server architecture described in the project report, with Django handling user interaction and backend processing, TF-IDF performing text transformation, Random Forest performing prediction, and the recommendation process returning relevant jobs.

28. Example of Complete Execution

Suppose a user has the following profile:

Education:
MCA

Skills:
Python, Django, SQL, Machine Learning

Experience:
0 years

Preference:
Software Developer

The system executes as follows:

Step 1

The user logs into the application.

Step 2

The system retrieves the user's profile.

Step 3

The profile information is combined into text.

MCA Python Django SQL Machine Learning
0 years Software Developer

Step 4

The text is processed using NLP techniques.

Step 5

TF-IDF converts the text into a numerical vector.

Step 6

The Random Forest model predicts a suitable job category.

For example:

Python Developer

Step 7

The system loads jobs from:

jobs.csv

Step 8

Each job's company, skills, location, salary, and description are combined.

Step 9

The job information is converted into TF-IDF vectors.

Step 10

Cosine similarity compares:

User Profile Vector
        VS
Job Vector

Step 11

Every job receives a similarity score.

Step 12

The jobs are sorted from highest to lowest score.

Step 13

The system selects the top five matching jobs.

Step 14

Django sends the results to the frontend.

Step 15

The user sees personalized recommendations such as:


Recommended Job: Python Developer

1. Python Developer       92%
2. Django Developer       88%
3. ML Developer           84%
4. Software Developer     79%
5. Data Analyst           74%


This completes the execution of the Job Recommendation System.


29. Why Multiple Techniques Are Used

The project does not depend on only one technique.

Each technique has a different purpose:

| Technique          | Purpose                                             |
| ------------------ | --------------------------------------------------- |
| Django             | Provides the web application                        |
| SQLite             | Stores application/user data                        |
| Pandas             | Reads and processes job datasets                    |
| NLP                | Processes textual profile and job information       |
| TF-IDF             | Converts text into numerical features               |
| Random Forest      | Predicts suitable job categories                    |
| Cosine Similarity  | Measures user-job similarity                        |
| Label Encoder      | Converts job labels between text and numerical form |
| Matplotlib/Seaborn | Displays graphs and analytics                       |

This combination allows the project to perform both job-role prediction and job-level matching.



30. Project Execution in One Line

The complete project execution can be summarized as:


User Profile
-> Preprocessing
-> NLP
-> TF-IDF
-> Feature Extraction
-> Random Forest Prediction
-> Load jobs.csv
-> Job TF-IDF
-> Cosine Similarity
-> Ranking
-> Top 5 Recommendations
-> Django Result Display

31. Future Enhancements

The project can be extended with:

* Real-time job portal integration
* Location-based recommendations
* Salary-based filtering
* Career growth prediction
* Multiple job portal integration
* Advanced NLP
* Transformer-based models
* Deep Learning
* Mobile application
* Multilingual recommendations
* Skill-gap analysis
* AI chatbot
* Personalized career guidance
* Continuous learning from user feedback
* Improved security and privacy

These enhancements are also identified in the project report as possible future improvements.


32. Conclusion

The Job Recommendation System Using LinkedIn User Profiles is an intelligent web-based application that automates the process of finding suitable employment opportunities.

The system starts with user registration and administrator activation. After login, the user provides professional information such as skills, education, experience, certifications, and job preferences. This information is processed using NLP techniques and converted into numerical features using TF-IDF.

The trained Random Forest model uses these features to predict a suitable job role. At the same time, the system processes available jobs from jobs.csv and represents them using TF-IDF. Cosine similarity is then used to compare the user's profile with available jobs. The jobs with the highest similarity scores are ranked and the top recommendations are displayed through the Django web interface.

Therefore, the system combines Django, NLP, TF-IDF, Random Forest, and cosine similarity to provide personalized job recommendations. It reduces the effort required for manual job searching and helps users identify job opportunities that are more closely related to their skills, qualifications, experience, and preferences.
