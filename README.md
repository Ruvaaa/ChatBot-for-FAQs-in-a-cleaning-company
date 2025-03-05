FAQ Chatbot

Overview

This FAQ Chatbot is built using Flask and spaCy to provide quick and accurate responses to frequently asked questions. It processes user queries and matches them with predefined answers to improve customer support and user engagement.

Features

Fast and efficient responses to FAQs

Natural language processing using spaCy

Web-based interface powered by Flask

Customizable question-answer pairs

Easy integration into websites or applications

Installation

Prerequisites

Ensure you have Python installed (Python 3.7 or later recommended). You also need Flask and spaCy.

Steps

Clone the repository:

git clone <repository_url>
cd faq-chatbot

Create and activate a virtual environment (optional but recommended):

python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate

Install dependencies:

pip install -r requirements.txt

Download the necessary spaCy model:

python -m spacy download en_core_web_sm

Run the Flask application:

python app.py

Open your browser and go to http://127.0.0.1:5000/ to access the chatbot.

Usage

Enter a question in the chatbot interface.

The bot processes the query and returns a relevant response.

If the question is not found, it provides a fallback message.

Configuration

Modify faq_data.json to add or update FAQs.

Customize Flask routes and UI in app.py and templates/ as needed.

Future Enhancements

Expand NLP capabilities with more advanced models.

Add a feedback mechanism to improve response accuracy.

Integrate with external databases for dynamic FAQs.

Contributing

Feel free to fork the project, make improvements, and submit pull requests!

License

This project is licensed under the MIT License.
