# 🩺 Multilingual Health Chatbot

This project presents an interactive and multilingual health chatbot built using Streamlit, designed to provide basic first aid and prevention advice for common ailments. The chatbot supports English, Hindi, and Hinglish interactions, offering personalized health guidance and an administrative dashboard for monitoring and content management.

## ✨ Features

### User Interface (Main App)

*   **User Authentication**: Secure login and signup system for individual users.
*   **Personalized Health Dashboard**: Users can input and manage their height, weight, age, gender, and blood group. The dashboard automatically calculates and displays BMI status.
*   **Multilingual Interaction**: Seamless communication in English, Hindi, and Hinglish. The chatbot automatically detects the input language and translates it for processing, then responds in the user's input language.
*   **Contextual Health Advice**: Provides first aid and prevention tips based on detected symptoms, with dynamic disclaimers and alerts tailored to the user's age (e.g., child, elderly).
*   **Feedback Mechanism**: Users can provide feedback (👍 or 👎) on bot responses, which is logged for quality improvement.
*   **Persistent Chat History**: All user queries, bot responses, and feedback are saved and loaded across sessions.
*   **Symptom Trend Visualization**: A personal dashboard displaying the top 5 most frequently reported symptoms over time, based on user queries.

### Admin Dashboard

*   **System Health Monitoring**: Overview of total registered users, total queries handled, and knowledge base size.
*   **Knowledge Base Management (CRUD)**: Administrators can easily add new symptoms/conditions with corresponding first aid and prevention advice, or delete existing entries.
*   **Analytics & Gaps**: 
    *   **Language Usage Distribution**: A pie chart showing the breakdown of queries by language (English, Hindi, Unknown).
    *   **Content Gap Analysis**: Identifies top unanswered queries (user inputs that did not match any symptoms in the knowledge base), highlighting areas where the KB can be expanded.
    *   **Bot Quality Monitoring**: Lists top disliked responses, allowing admins to review and improve the bot's accuracy and helpfulness.
*   **User Activity & Management**: Allows admins to inspect individual user profiles and review their last 5 queries.

## 🚀 Getting Started

### Prerequisites

*   Python 3.7+
*   `pip` (Python package installer)
*   An ngrok account and authentication token (for local development/demo) - you can get one from [ngrok.com](https://ngrok.com/)

### Installation

1.  **Clone the repository** (if applicable, or download `Milestone3_Auth.py`):
    ```bash
    # Assuming you have git installed
    git clone <your-repository-url>
    cd <your-repository-name>
    ```

2.  **Install dependencies**: All necessary Python packages are installed automatically by the provided script.
    ```python
    # This line is in cell JkSspGXr6amC of the notebook
    !pip install streamlit transformers sentencepiece torch pyngrok > /dev/null
    ```

3.  **Set up ngrok**: Your ngrok authentication token is essential to expose your local Streamlit app to the internet.
    ```python
    # This line is in cell snTbvK_S6srt of the notebook
    from pyngrok import ngrok
    NGROK_AUTH_TOKEN = "YOUR_NGROK_AUTH_TOKEN" # 🔑 Replace with your own token
    ngrok.set_auth_token(NGROK_AUTH_TOKEN)
    ```
    *Make sure to replace `YOUR_NGROK_AUTH_TOKEN` with your actual token.*

### Running the Application

1.  **Save the Streamlit code**: Ensure the main application code is saved as `Milestone3_Auth.py`.
    (In a Colab environment, this is typically done using `%%writefile Milestone3_Auth.py` in the relevant cell).

2.  **Start Streamlit and ngrok**: Execute the following code to run the Streamlit app and get a public URL.
    ```python
    from pyngrok import ngrok, conf
    import os, threading, time

    # Disconnect all previous ngrok tunnels for a clean start
    for t in ngrok.get_tunnels():
        ngrok.disconnect(t.public_url)
    print("✅ All previous ngrok tunnels closed.")

    def start_streamlit():
        os.system("streamlit run Milestone3_Auth.py --server.port 8501 --server.headless true")

    threading.Thread(target=start_streamlit, daemon=True).start()
    time.sleep(8) # Give Streamlit time to start
    public_url = ngrok.connect(8501).public_url
    print("🌐 Public URL:", public_url)
    ```

3.  **Access the application**: Open the `Public URL` printed in your browser.

## 🔒 Authentication

### User Login/Signup

*   New users can sign up with a username and password.
*   Existing users can log in.
*   User profiles (health metrics) and chat histories are persistent.

### Admin Login

*   **Username**: `admin`
*   **Password**: `healthbotadmin123` (Note: This is a hardcoded default for demonstration purposes. In a production environment, this should be securely managed).

## 🛠️ Technology Stack

*   **Web Framework**: [Streamlit](https://streamlit.io/)
*   **Natural Language Processing (NLP)**: [Hugging Face Transformers](https://huggingface.co/transformers/) (MarianMT models for English-Hindi translation)
*   **Data Manipulation**: [Pandas](https://pandas.pydata.org/)
*   **Visualization**: [Altair](https://altair-viz.github.io/)
*   **Deployment/Tunneling (for local dev)**: [Pyngrok](https://pyngrok.readthedocs.io/en/latest/)
*   **Persistence**: JSON files (`users.json`, `metrics.json`) for user data and chat history.

## 📝 License

This project is open-source and available under the [MIT License](LICENSE).

---

**Disclaimer**: This chatbot is intended for general wellness advice and informational purposes only. It is **not** a substitute for professional medical advice, diagnosis, or treatment. Always seek the advice of your physician or other qualified health provider with any questions you may have regarding a medical condition.
Generate README Content: Create the complete Markdown content for the README.md file, detailing the project title, description, user and admin features, technology stack, setup instructions, usage guidelines, and any relevant disclaimers. This will include information about authentication (admin credentials, how to sign up), the knowledge base, multilingual support, and persistence.
Save README File: Write the generated Markdown content to a new file named README.md in the current directory.
Final Task: Confirm that the README.md file has been successfully created and saved, and provide instructions on how to view it.
 
 
