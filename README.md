# Survey Feedback Analyzer

## Project Overview

The Survey Feedback Analyzer is a Python project that analyzes customer feedback and ratings. It demonstrates fundamental Python programming concepts, including dictionaries, lists, loops, functions, string manipulation, and basic data analysis.

## Objectives

- Store customer feedback and ratings using a dictionary.
- Add new feedback entries dynamically.
- Clean feedback text by removing punctuation, extra spaces, and uppercase letters.
- Count feedback entries containing specific words.
- Calculate the average customer rating.
- Identify the feedback with the longest comment.
- Extract unique words used across all feedback entries.

## Technologies Used

- Python 3
- Jupyter Notebook

## Project Files

- `Survey_Feedback_Analyzer.ipynb` — Contains the complete Python code for the assignment.
- `Module End Assignment 4_Python Fundamentals- Survey Feedback Analyzer.pdf` — Assignment instructions.
- `README.md` — Project documentation.

## Step 1: Preloaded Feedbacks

### Code

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

### Output

The dictionary containing 10 preloaded feedback entries, customer names, serial numbers, and ratings is displayed.

## Step 2: Add More Feedbacks

### Code

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

### Sample Input

    How many more feedbacks do you want to add? 2
    Enter name: Anshad
    Enter written feedback: Good service and friendly staff
    Enter rating (1-5): 5
    Enter name: Archana
    Enter written feedback: Poor service and slow response
    Enter rating (1-5): 2

### Output

Two additional feedback entries are added successfully. The dictionary now contains 12 feedback entries with serial numbers from 1 to 12.

## Step 3: Clean Feedback Text

### Code

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

### Output

The feedback text is cleaned by removing the specified punctuation, reducing extra spaces, removing leading and trailing spaces, and converting all text to lowercase.

The cleaned feedback entries are:

    [
        'very good service',
        'poor support not happy',
        'great experience will come again',
        'okay okay',
        'not bad',
        'excellent care excellent staff',
        'good food and good ambience',
        'poor response and poor handling of issue',
        'satisfied but could be better',
        'good support quick service',
        'good service and friendly staff',
        'poor service and slow response'
    ]

## Step 4: Count Word Occurrences in Feedback Entries

### Code

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

### Output

    Feedbacks containing 'good': 4
    Feedbacks containing 'poor': 3
    Feedbacks containing 'excellent': 1

The function counts the number of feedback entries containing each specified whole word.

## Step 5: Final Analysis

### Code

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

### Output Summary

- Total feedback entries: 12
- Average rating: 3.4166666666666665
- Average rating rounded to two decimal places: 3.42 out of 5
- Longest feedback: `poor response and poor handling of issue`
- Word count of the longest feedback: 7
- Number of unique words: 32

### Unique Words

    [
        'very', 'good', 'service', 'poor', 'support', 'not', 'happy',
        'great', 'experience', 'will', 'come', 'again', 'okay', 'bad',
        'excellent', 'care', 'staff', 'food', 'and', 'ambience',
        'response', 'handling', 'of', 'issue', 'satisfied', 'but',
        'could', 'be', 'better', 'quick', 'friendly', 'slow'
    ]

## Python Concepts Demonstrated

- Dictionaries and lists
- User input and type conversion
- For loops
- Functions and return statements
- Conditional statements
- String manipulation and text cleaning
- Word counting
- Average calculation
- Finding the longest comment
- Extracting unique words

## Conclusion

The Survey Feedback Analyzer demonstrates how Python can be used to organize, clean, and analyze customer feedback. The project calculates the average customer rating, counts feedback entries containing specific words, identifies the longest comment, and extracts unique words.

This project provides practical experience with fundamental Python concepts and demonstrates their application in basic data analysis.

## Author

Deepthi
