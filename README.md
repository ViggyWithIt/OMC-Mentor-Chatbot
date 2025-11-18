# OMC Mentor Feedback Chatbot
A project by Julian Vignes and Sharanya Chatterjee

This is an AI-powered chatbot we built to help volunteer mentors at the Orlando Math Circle.

## The Problem
My friend and I are both volunteers at OMC, and we know that giving good, consistent feedback to the student facilitators is really important but also takes a lot of time. We wanted to create a tool that could help automate this, making sure the feedback was always high-quality and aligned with OMC's inquiry-based teaching principles.

## Our Solution
We built this chatbot to analyze a transcript from a teaching session. It uses a knowledge base of real feedback examples to generate its own supportive and concrete suggestions for the mentor. The goal is for it to feel like you're getting advice from an experienced, friendly colleague.

#### How It Works (the tech stuff :))
The whole system is built on a RAG (Retrieval-Augmented Generation) architecture.

1.  **The knowledge base-** We started with a big JSON file (`chatbot_training.json`) filled with dozens of real-world examples of transcripts and the expert feedback they received. This is the "brain" of the system

2.  **Vector Embeddings:** We used LangChain and FAISS to turn all that text into vector embeddings. This basically lets the program search for examples based on their meaning, not just keywords

3.  **RAG:** when you give it a new transcript, the system finds the 3 most similar examples from our knowledge base.

4.  **Generation-** Finally, it sends those examples, the new transcript, and a lengthy prompt to GPT-4o-mini. The prompt tells the model to act like an OMC mentor and use the examples to create its own feedback, structured with "Observation," "Feedback," and "Suggestion" sections.

### Project files
*   `omc_chatbot.ipynb` - the main Jupyter Notebook with all the python code
*   `chatbot_training.json` - our knowledge base of feedback examples.
*   `medium_alex_transcript.pdf` - an example transcript we used for testing
*   `requirements.txt` - all the packages you need to install

### How to Use
To get this running, you'll need to clone the repo first.
```
git clone https://github.com/ViggyWithIt/OMC-Mentor-Chatbot
```
Then install the required packages.
```
pip install -r requirements.txt
```
After that, just run the `omc_chatbot.ipynb` notebook. It will ask you for your OpenAI API key when you run it (we didn't want to hardcode ours in there for obvious reasons).

### Future Ideas
- It would be very interesting to build a simple web interface with Streamlit so mentors don't have to run code
- Potentially fine-tune a smaller open-source model on our data to save on API costs

## Built By
- Julian Vignes
- Sharanya Chatterjee
