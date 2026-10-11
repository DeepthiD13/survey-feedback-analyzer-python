# Survey Feedback Analyzer

## Project Overview

The Survey Feedback Analyzer is a Python project that collects customer feedback, cleans text data, counts specific words, and performs basic analysis of customer ratings and comments.

This project demonstrates the use of Python dictionaries, lists, loops, conditional statements, functions, string methods, and basic data analysis.

## Objectives

- Store customer names, feedback comments, serial numbers, and ratings.
- Add new customer feedback dynamically.
- Clean feedback text by removing punctuation and extra spaces and converting text to lowercase.
- Count feedback entries containing specific words.
- Calculate the average customer rating.
- Identify the longest feedback comment by word count.
- Extract unique words used across all feedback entries.

## Technologies Used

- Python 3
- Jupyter Notebook

## Project Files

- `Survey_Feedback_Analyzer.ipynb` — Jupyter Notebook containing the complete Python assignment and outputs.
- `README.md` — Project documentation.

## Step 1: Preload Feedback Data

    # Step 1: Preloaded Feedbacks

    feedback_data = {
        'S_No': [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
        'Name': ['Ravi', 'Meera', 'Sam', 'Anu', 'Raj', 'Divya', 'Arjun', 'Kiran', 'Leela', 'Nisha'],
        'Feedback': [
            '   Very GOOD Service!!!',
            'poor support,        not happy   ',
            'GREAT experience! will come again.',
            'okay     okay...',
            '   not    BAD',
            'Excellent care, excellent staff!',
            'good food and good ambience!',
            'Poor response and poor handling of issue',
            'Satisfied. But could be better.',
            'Good support... quick service.'
        ],
        'Rating': [5, 2, 5, 3, 2, 5, 4, 1, 3, 4]
    }

    print(feedback_data)

This step creates a dictionary containing the initial 10 customer feedback entries, including their serial numbers, names, comments, and ratings.

## Step 2: Add More Feedbacks

    # Step 2: Add More Feedbacks

    n = int(input("How many more feedbacks do you want to add? "))

    for i in range(n):
        s_no = len(feedback_data['S_No']) + 1
        name = input("Enter name: ")
        feedback = input("Enter written feedback: ")
        rating = int(input("Enter rating (1-5): "))

        feedback_data['S_No'].append(s_no)
        feedback_data['Name'].append(name)
        feedback_data['Feedback'].append(feedback)
        feedback_data['Rating'].append(rating)

    print(feedback_data)

Two additional feedback entries were added:

- Anshad — Good service and friendly staff — Rating: 5
- Archana — Poor service and slow response — Rating: 2

The dataset contains 12 feedback entries after this step.

## Step 3: Clean Feedback Text

    # Step 3: Clean Feedback Text

    for i in range(len(feedback_data['Feedback'])):
        text = feedback_data['Feedback'][i]
        text = text.replace('.', '')
        text = text.replace(',', '')
        text = text.replace('!', '')
        text = text.replace('?', '')
        text = ' '.join(text.split())
        text = text.lower()
        feedback_data['Feedback'][i] = text

    print(feedback_data)

This step removes the specified punctuation, reduces multiple spaces to a single space, removes leading and trailing spaces, and converts feedback comments to lowercase.

Example:

- Before cleaning: `   Very GOOD Service!!!`
- After cleaning: `very good service`

## Step 4: Count Feedback Entries Containing Specific Words

    # Step 4: Count Word Occurrences in Feedback Entries

    def count_word_in_feedbacks(word):
        count = 0
        for feedback in feedback_data['Feedback']:
            if word.lower() in feedback.lower().split():
                count += 1
        return count

    print("Feedbacks containing 'good':", count_word_in_feedbacks("good"))
    print("Feedbacks containing 'poor':", count_word_in_feedbacks("poor"))
    print("Feedbacks containing 'excellent':", count_word_in_feedbacks("excellent"))

Expected output:

    Feedbacks containing 'good': 4
    Feedbacks containing 'poor': 3
    Feedbacks containing 'excellent': 1

The function counts the number of feedback entries containing each specified word. Each entry is counted once per search word, even if the word appears multiple times in that entry.

## Step 5: Final Analysis

    # Step 5: Final Analysis

    print("Final cleaned feedback data:")
    print(feedback_data)

    total_rating = sum(feedback_data['Rating'])
    average_rating = total_rating / len(feedback_data['Rating'])
    print("\nAverage rating:", average_rating)

    longest_feedback = ""
    max_word_count = 0

    for feedback in feedback_data['Feedback']:
        word_count = len(feedback.split())
        if word_count > max_word_count:
            max_word_count = word_count
            longest_feedback = feedback

    print("\nFeedback with the longest comment:", longest_feedback)
    print("Word count:", max_word_count)

    unique_words = []

    for feedback in feedback_data['Feedback']:
        for word in feedback.split():
            if word not in unique_words:
                unique_words.append(word)

    print("\nUnique words used across all feedbacks:")
    print(unique_words)

## Results

| Analysis | Result |
|---|---|
| Initial feedback entries | 10 |
| Additional feedback entries | 2 |
| Total feedback entries | 12 |
| Feedback entries containing 'good' | 4 |
| Feedback entries containing 'poor' | 3 |
| Feedback entries containing 'excellent' | 1 |
| Average rating | 3.4166666666666665 |
| Average rating rounded to two decimal places | 3.42 out of 5 |
| Longest feedback comment | poor response and poor handling of issue |
| Word count of longest comment | 7 |
| Number of unique words | 32 |

## How to Run the Project

1. Open Jupyter Notebook.
2. Open `Survey_Feedback_Analyzer.ipynb`.
3. Run the five code cells in order, from Step 1 to Step 5.
4. During Step 2, enter the number of additional feedback entries and provide the requested names, comments, and ratings.
5. Review the output after each step.

Important: Run Step 2 only once during a fresh execution of the notebook to avoid adding duplicate entries.

## Concepts Demonstrated

- Python dictionaries and lists
- User input and type conversion
- Loops and conditional statements
- Functions and return values
- String cleaning and normalization
- Word counting and list operations
- Average calculation and basic data analysis

## Conclusion

The Survey Feedback Analyzer demonstrates how Python can be used to organize and analyze customer feedback. The project successfully stores 12 feedback entries, cleans the comments, counts entries containing selected words, calculates the average rating, identifies the longest comment, and extracts unique words.

This assignment provides practical experience with Python fundamentals and basic text data analysis.
