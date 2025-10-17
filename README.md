### Gemini Flash Exp Chatbot

This project is an enhanced web-based chat application designed to interact with the Gemini Flash API. It provides a user-friendly interface for sending prompts and receiving responses, featuring comprehensive chat management, persistent settings, and message enhancements. This tool is ideal for academic exploration of AI capabilities, rapid prototyping, and demonstrating web development skills.

#### Summary

The Gemini Flash Exp Chatbot is a single-page HTML application that leverages client-side JavaScript to communicate with Google's Gemini API. It offers a robust set of features including a collapsible settings panel for API key management, system prompt configuration, temperature control, and max token limits. Chat history is preserved across sessions, and users can clear or export their conversations. Message timestamps and bot response copy functionality improve user experience, along with real-time character and message counters.

#### Setup

1.  **Obtain a Gemini API Key**: Visit the Google AI Studio (or equivalent Google Cloud Console section) to generate your API key. This key is necessary for the chatbot to communicate with the Gemini API.
2.  **Download the project**: Save the `index.html` file to your local machine.
3.  **Open in Browser**: Simply open the `index.html` file in any modern web browser (e.g., Chrome, Firefox, Edge, Safari). No server-side setup or additional dependencies are required.

#### Usage

1.  **Enter API Key**: Upon loading the page, input your Gemini API Key into the designated field. You can use the "Show API Key" checkbox to toggle visibility. Your API key will be saved locally in your browser's `localStorage`.
2.  **Configure Settings (Optional)**:
    *   Click "Settings" to expand the panel.
    *   **System Prompt**: Enter a system prompt (e.g., "You are a helpful academic assistant specialized in computer science.") to guide the AI's persona or instructions. This will be included in API requests.
    *   **Temperature**: Adjust the slider to control the randomness of the AI's responses (0 for deterministic, 2 for highly creative).
    *   **Max Output Tokens**: Set the maximum length of the AI's generated response.
    *   All settings are automatically saved to `localStorage`.
3.  **Start Chatting**: Type your message into the input textarea. The character counter will show remaining characters (max 2000). Press "Send" or hit `Enter` to send your message.
4.  **View Responses**: The chatbot's responses will appear in the chat history area. Each message includes a timestamp. Bot messages also have a "Copy" button to easily copy their content to your clipboard.
5.  **Manage Chat**:
    *   **Message Counter**: Displays the total number of messages in the current chat session.
    *   **Clear Chat**: Click "Clear Chat" to delete all messages from the history (requires confirmation).
    *   **Export Chat**: Click "Export Chat" to download your entire conversation history, along with current settings, as a JSON file.
6.  **Persistence**: Your API key, chat settings, and chat history are automatically saved to your browser's `localStorage` and will be restored when you revisit the page.

#### Main Code Logic

The application's core logic is implemented in a single `script` block within `index.html`, ensuring all features are self-contained and client-side.

*   **DOM Manipulation**: Extensive use of `document.getElementById` to access and manipulate UI elements. Messages are dynamically created and appended to the `#chat-messages` div.
*   **API Integration**: The `sendMessage()` function is responsible for constructing the API request body. It retrieves the API key, user input, and current settings (system prompt, temperature, max tokens) from the UI. The request body is structured according to the Gemini API specifications, including `contents`, `generationConfig`, and conditionally `systemInstruction`. A `fetch` API call sends the request to the `gemini-pro:generateContent` endpoint.
*   **Persistence (`localStorage`)**:
    *   `saveSettings()` and `loadSettings()`: Manage the storage and retrieval of the Gemini API key (under `geminiApiKey`) and other chatbot settings (system prompt, temperature, max tokens, bundled as `chatSettings`) in `localStorage`.
    *   `saveChatHistory()` and `loadChatHistory()`: Handle the serialization and deserialization of the `chatHistory` array to/from `localStorage`.
*   **Chat Management**:
    *   `clearChatBtn` event listener: Prompts user confirmation, clears the `chatHistory` array, removes `chatHistory` from `localStorage`, and empties the `#chat-messages` div.
    *   `exportChatBtn` event listener: Gathers current settings and `chatHistory`, formats them as JSON, creates a Blob, and triggers a file download.
*   **Message Enhancements**:
    *   `displayMessage()`: This function is central to rendering messages. It creates `div` elements, applies appropriate styling (`user-message` or `bot-message`), adds a formatted timestamp (using `formatTime`), and for bot messages, inserts a "Copy" button (`copyTextToClipboard` function handles clipboard interaction). Messages are added to `chatHistory` and `localStorage` unless explicitly told not to.
    *   `updateCharCount()`: Real-time updates the character counter for the user input.
    *   `updateMessageCount()`: Displays the current number of messages in the chat.
*   **Settings Panel**: A `settingsPanelToggle` event listener manages the visibility of the `#settings-panel` div, updating an arrow icon for visual feedback.
*   **Event Handling**: `DOMContentLoaded` ensures settings and history are loaded on page init. Event listeners are attached to input fields (`input`), buttons (`click`), and the user input textarea (`keydown` for Enter, `input` for char count) to trigger core functionalities.

#### License

MIT License
<br>
Copyright (c) 2023-2024 Your Name/Organization
<br>
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:
<br>
The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
<br>
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

#### Contact

For questions or feedback, please contact [Your Name/Email/GitHub Profile].