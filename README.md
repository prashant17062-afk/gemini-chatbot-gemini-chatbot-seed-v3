# Gemini 2.0 Flash Exp Chatbot

This project is a fully functional web-based AI chatbot powered by the Google Gemini 2.0 Flash Exp API. It provides a clean, responsive chat interface where users can interact with the Gemini model after setting up their API key.

## Features

*   **API Key Management**: Securely store and retrieve your Gemini API key from `localStorage`.
*   **Dynamic UI**: Enable/disable chat functionality based on API key availability.
*   **Real-time Chat**: Send messages to the Gemini 2.0 Flash Exp model and receive responses.
*   **Typing Indicator**: Visually indicate when the bot is processing a response.
*   **Error Handling**: Catch and display common API errors, including invalid API keys.
*   **Responsive Design**: Built with Bootstrap 5 for a mobile-friendly and modern user experience.
*   **Message Styling**: Distinctive styling for user and bot messages for improved readability.
*   **Persistence**: API key is saved locally, so you don't have to re-enter it on page refresh.

## Usage

1.  **Get an API Key**: Visit [https://ai.google.dev/](https://ai.google.dev/) to obtain your free Google Gemini API key.
2.  **Set API Key**:
    *   Open `index.html` in your web browser.
    *   Enter your Gemini API key into the "Gemini API Key" input field.
    *   Click the "Set Key" button. The status will change to "API Key: Set ✓".
3.  **Start Chatting**:
    *   Once the API key is set, the message input and send button will become active.
    *   Type your message into the input field and press Enter or click "Send".
    *   The bot's response will appear in the chat history.

## License

This project is open-source and available under the MIT License.