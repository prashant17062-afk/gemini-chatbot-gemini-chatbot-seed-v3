# Gemini 2.0 Flash Exp Chatbot

## Summary
This project delivers a fully functional AI chatbot application built with HTML, CSS (Bootstrap 5), and JavaScript, leveraging the Google Gemini 2.0 Flash Exp API. Designed for academic grading, it demonstrates critical web development skills including API integration, client-side data persistence, responsive UI design, and robust error handling.

## Setup
To run this chatbot locally:
1.  **Save the file:** Save the provided `index.html` content into a file named `index.html` on your computer.
2.  **Open in browser:** Open the `index.html` file using any modern web browser (e.g., Chrome, Firefox, Edge).
3.  **Obtain API Key:** Visit [https://ai.google.dev/](https://ai.google.dev/) to get a free Google Gemini API Key.
4.  **Set API Key:** On the loaded page, enter your Gemini API Key into the "Enter your Google Gemini API Key" password field and click the "Set API Key" button. The key will be securely saved in your browser's local storage.

## Usage
Once the `index.html` file is open in your browser and your API key is set:
1.  **API Key Setup:** Enter your Google Gemini API key into the input field and click "Set API Key". The status will change to "API Key: Set ✓" and the chat input will become active.
2.  **Chatting:** Type your message into the "Type your message..." input field.
3.  **Sending Messages:** Click the "Send" button or press `Enter` to send your message to the AI.
4.  **AI Response:** The AI's response will appear in the chat window, preceded by a "AI is typing..." indicator.
5.  **Persistence:** Your API key is saved in local storage, so you typically only need to set it once per browser.

## Main Code Logic

### HTML Structure (`index.html`)
The HTML document establishes a clean and responsive user interface using Bootstrap 5.
-   **API Key Section:** Contains a password input field (`#api-key-input`), a button (`#set-api-btn`) to save the key to `localStorage`, a status indicator (`#api-status`), and a link to `ai.google.dev`.
-   **Chat Interface:** Features a scrollable container (`#chat-messages`) for displaying messages, a typing indicator (`#typing-indicator`), a text input field (`#user-input`), and a send button (`#send-btn`).

### JavaScript Logic
The core functionality is implemented in the embedded JavaScript:
-   **API Key Management:**
    -   `apiKey` variable stores the currently active API key.
    -   `loadApiKey()` retrieves the key from `localStorage` on page load, updating the UI and enabling/disabling chat inputs accordingly.
    -   `saveApiKey()` stores the entered key in `localStorage` under the key `'geminiApiKey'`, updates the UI, and enables chat.
-   **Chat UI Handling:**
    -   `updateApiStatus(isSet)`: Dynamically changes the API key status message and color.
    -   `toggleChatInputs(enable)`: Controls the `disabled` state of the chat input and send button.
    -   `addMessage(sender, text)`: Appends new messages to the `#chat-messages` container. It dynamically styles messages based on the `sender` ('user' or 'bot'), aligning user messages to the right with a blue background and bot messages to the left with a light gray background, utilizing Bootstrap's flex utilities.
    -   `showTypingIndicator()` and `hideTypingIndicator()`: Manage the visibility of the "AI is typing..." message.
-   **Real API Integration (`sendMessage()`):**
    -   Constructs a `POST` request to the Google Gemini API endpoint (`https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash-exp:generateContent`).
    -   The API key is appended as a query parameter (`?key=`).
    -   The request body is formatted as `{'contents': [{'parts': [{'text': userMessage}]}]}`.
    -   Handles the `fetch` call, displaying a typing indicator during the request.
    -   Parses the API response, extracting the bot's message from `data.candidates[0].content.parts[0].text`.
    -   Adds both user and bot messages to the chat interface.
-   **Error Handling:**
    -   A `try...catch` block handles network errors during the `fetch` call.
    -   Checks `response.ok` for HTTP errors (e.g., 400, 403, 500) and displays specific error messages in the chat, particularly for invalid API keys.

### Persistence
The Google Gemini API Key is stored and retrieved from the browser's `localStorage` to persist across sessions, providing a seamless user experience.

## License
This project is licensed under the MIT License. See the `index.html` footer for details.

## Contact
For any questions or feedback, please reach out to the project maintainer.