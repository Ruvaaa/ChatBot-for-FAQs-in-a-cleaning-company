from flask import Flask, render_template, request, jsonify
import spacy

app = Flask(__name__)
nlp = spacy.load("en_core_web_md")

faqs = {
    "What is your return policy?": "Our return policy allows you to return products within 30 days of purchase.",
    "How do I contact support?": "You can contact support via email at support@example.com.",
    "Where are you located?": "We are located in New York City.",
    "How much are your washing machines?": "Our washing machines cost from $150 to $500 depending on the model.",
    "Thank you": "You are welcome.",
    "How much do you hoovers cost?": "Our hoovers cost from $30 to $200 depending on the model and quality.",
    "Do you take credit or payment plans?": "We offer personalized payment plans according to a person's needs, but do not sell on Credit.",
    "What is your cheapest automated cleaning bot?": "Our cheapest automated cleaning bot would be the H33 SAMSUNG Hoover ECOM.",
    "Which washing machine brand and model would you suggest for someone staying alone?": "I would suggest the LG WASH AND GO MINI, a small capacity washing machine that doesn't use too much water, power, or space.",
    "My power vacuum is making a lot of noise, what do I do to fix it?": "We apologize for the inconvenience. I suggest checking the vacuum's pipes and using a stick to clear any blockages."
}

small_talk_phrases = {
    "hello": "Hi! How can I assist you today?",
    "hi": "Hello! How can I help you?",
    "how are you": "I'm just a bot, but I'm doing great! How about you?",
    "bye": "Goodbye! Have a great day!"
}

def small_talk(user_input):
    for phrase, response in small_talk_phrases.items():
        if phrase in user_input.lower():
            return response
    return None

def faq_chatbot(user_input):
    small_talk_response = small_talk(user_input)
    if small_talk_response:
        return small_talk_response

    doc_input = nlp(user_input)
    best_match = None
    highest_similarity = 0

    for question, answer in faqs.items():
        doc_question = nlp(question)
        similarity = doc_input.similarity(doc_question)

        if similarity > highest_similarity:
            highest_similarity = similarity
            best_match = answer

    if highest_similarity > 0.7:
        return best_match
    else:
        return "I'm sorry, I didn't understand that. Can you rephrase?"

@app.route('/')
def home():
    return render_template('okay.html')

@app.route('/chat', methods=['POST'])
def chat():
    user_message = request.json.get("message")
    response = faq_chatbot(user_message)
    return jsonify({"response": response})

if __name__ == '__main__':
    app.run(debug=True)
