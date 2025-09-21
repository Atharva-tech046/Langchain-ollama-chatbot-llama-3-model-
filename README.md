# LangChain Terminal Chatbot with Ollama & Llama 3

A simple yet powerful command-line AI chatbot that leverages the **LangChain** framework to interact with a locally running **Llama 3** model via **Ollama**. This project, `langchain-ollama-chatbot`, demonstrates how to build a stateful conversational agent that remembers the context of the dialogue. 🚀

---

## ✨ Features

* **Conversational Memory**: The chatbot maintains the history of the current conversation, allowing for contextual follow-up questions.
* **Local First**: Runs entirely on your local machine using [Ollama](https://ollama.com/), ensuring privacy and no API costs.
* **LangChain Powered**: Utilizes the LangChain Expression Language (LCEL) for a clean and modular chain construction.
* **Simple & Lightweight**: A single Python script with minimal dependencies, making it easy to understand and run.
* **Easy to Customize**: You can easily swap out the LLM (e.g., to `mistral` or `gemma`) or modify the prompt template to change the chatbot's personality.

---

## ⚙️ Getting Started

Follow these instructions to get a copy of the project up and running on your local machine.

### Prerequisites

1.  **Python**: Ensure you have Python 3.8+ installed. You can check your version by running `python3 --version` or `python --version`.
2.  **Ollama**: You must have [Ollama](https://ollama.com/) installed and running on your system.
3.  **Llama 3 Model**: Pull the Llama 3 model by running the following command in your terminal:
    ```sh
    ollama pull llama3
    run ollama llama3
    ```

### 📦 Installation

These steps include setting up a virtual environment, which is the recommended way to handle Python project dependencies.

1.  **Clone the repository:** (Replace `your-username` with your actual GitHub username)
    ```sh
    git clone [https://github.com/your-username/langchain-ollama-chatbot.git](https://github.com/your-username/langchain-ollama-chatbot.git)
    ```

2.  **Navigate into the project directory:**
    ```sh
    cd langchain-ollama-chatbot
    ```

3.  **Create and Activate a Virtual Environment:** This isolates the project's dependencies from your system.

    * First, create the environment:
        ```sh
        python3 -m venv chatbot 
        ```
    * Next, activate it. The command differs based on your operating system:

        * **On macOS / Linux:**
            ```sh
            source chatbot/bin/activate
            ```
        * **On Windows (Command Prompt or PowerShell):**
            ```sh
            .\venv\Scripts\activate
            ```
    * *(Your terminal prompt should now change to show `(venv)` at the beginning.)*

4.  **Install Required Packages:**

    * First, ensure you have a `requirements.txt` file in your project directory with this content:
        ```
        langchain-core
        langchain-ollama
        ```
    * Now, install the packages into your active virtual environment:
        ```sh
        pip install langchain langchain-ollama ollama 
        ```

---

## ▶️ Usage

1.  Make sure your Ollama application is running in the background and that your virtual environment is activated (you should see `(venv)` in your prompt).

2.  Run the chatbot script from your terminal:
    ```sh
    python3 main.py  # Or whatever you name your script
    ```

3.  Start chatting! Type your message and press Enter. To end the session, type `exit`.

    *(**Tip**: If the script gets stuck, you can force it to stop by pressing `Ctrl+C`.)*

4.  When you're finished, you can deactivate the virtual environment by simply typing:
    ```sh
    deactivate
    ```

**Example Interaction:**
```
(venv) $ python3 main.py
Welcome to the AI ChatBot , Type 'exit' to quit. 
You: Hi, my name is Alex.
Bot:  Hello Alex! It's nice to meet you. How can I help you today?
You: What is my name?
Bot:  Your name is Alex.
You: exit
(venv) $ deactivate
$
```

---

## 🛠️ How It Works

This chatbot operates on a simple yet effective principle:

1.  **Prompt Template**: A `ChatPromptTemplate` is defined to structure the input to the LLM. It includes a placeholder for the ongoing `context` (conversation history) and the new `question`.
2.  **LLM Initialization**: The `OllamaLLM` class connects to the local Ollama service and specifies that we want to use the `llama3` model.
3.  **LangChain Expression Language (LCEL)**: The `prompt` and `model` are chained together using the pipe (`|`) operator. This means the output of the prompt formatting is directly fed as input to the model.
4.  **Conversation Loop**: The `handle_coversation` function runs an infinite loop that:
    * Accepts user input.
    * Invokes the chain with the current `context` and the new `user_input`.
    * Prints the AI's response.
    * Crucially, it appends both the user's question and the AI's answer to the `context` string, ensuring the history is available for the next turn.

---

## 💡 Contributing

Contributions are welcome! If you have ideas for improvements, feel free to fork the repository and submit a pull request.

Some ideas for future enhancements:
* Add a simple web interface using **Gradio** or **Streamlit**.
* Implement more robust error handling.
* Add a command to clear the conversation history.

---

## 📄 License

This project is licensed under the MIT License. See the `LICENSE` file for details.
