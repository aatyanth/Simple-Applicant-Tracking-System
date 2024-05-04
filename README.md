# Simple Applicant Tracking System (ATS)

Utilizing NLP and ML algorithms, this simple Python program, when provided with a job description and resume, will provide a score from
0-5 on how well the provided resume matches the job description.

## Code Breakdown
### PDF To Text Conversion
- This program utilizes the `pdfminer` module to convert any the provided PDF files (Job description and Resume) to text

### Preprocessing Text
- Using the `NLTK` Python module, I removed `stopwords` and lemmatized words
- The purpose of removing `stopwords` is to ensure that commonly used words such as "the", "and", "yours", etc don't influence the results of the match
- `Lemmatizing` words involves reducing them to their root (Ex: Starts --> Start and Developed --> Develop)
  - The purpose of `lemmatizing` words is to ensure consistency in the type of words between the resume and job description

### Extracting Keywords
- Using the `sklearn` Python module, I used the `tfidf` algorithm to extract keywords from both the resume and job description
  - This is essential for the next step

 ### Keyword Matching
 - After extracting keywords from the job description and resume, I developed a keyword-matching algorithm that uses the keywords from the previous step to identify how  many keywords match
 - This algorithm returns a percentage number representing how well the keywords from the job description and resume match

### Score Creation
- Finally, using sample resumes that are good and bad fits for the job, this model trains itself on what to base the score off of
- Then, these sample resumes' match percentages and the input resume's match percentage are passed into an algorithm that uses the `scipy` module to calculate the percentile score of the input resume with respect to the sample resumes
- Finally, this algorithm uses a for loop and conditional statements to assign the score from 0-5 based on the percentile score of the input resume
