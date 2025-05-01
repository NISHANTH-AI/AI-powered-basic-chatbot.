# AI-powered-basic-chatbot.
Simple CSV-based Chatbot using Python and Pandas. This chatbot reads a dataset of questions and answers from a CSV file, processes user input, and returns matching responses. It supports case-insensitive matching and runs interactively in the console. Built for beginners to understand basic NLP and file handling in Python.
from google.colab import files
uploaded = files.upload()

import pandas as pd

# Load the dataset
data = pd.read_csv('/content/chat_bot_csv (3)')

# Convert all questions to lowercase for case-insensitive matching
data['Question'] = data['Question'].str.lower()

# Function to get response from chatbot
def get_response(user_input):
    user_input = user_input.lower().strip()
    if user_input in data['Question'].values:
        return data.loc[data['Question'] == user_input, 'Answer'].values[0]
    return "Sorry, I don't understand that yet."

# Start the chatbot
print("Chatbot: Hello! Type 'exit' to end the conversation.")

while True:
    user_input = input("You: ")
    if user_input.lower() == 'exit':
        print("Chatbot: Goodbye!")
        break
    response = get_response(user_input)
    print("Chatbot:", response)
