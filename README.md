# Gemini 1.5 Flash Exp Chatbot

This is an enhanced web-based chat interface for the Google Gemini 1.5 Flash API. It provides a user-friendly way to interact with the AI, offering several features for improved usability, management, and persistence.

## Summary

The Gemini 1.5 Flash Exp Chatbot allows users to converse with Google's Gemini 1.5 Flash model directly from their browser. It includes robust client-side storage for chat history and settings, a collapsible settings panel for API configuration, and various message enhancements for a richer user experience.

## Features

1.  **Settings Panel:**
    *   **Collapsible Design:** A `details` element allows the settings panel to be easily expanded or collapsed.
    *   **API Key Management:** Input field for the Google Gemini API Key with a checkbox to show/hide the key for security.
    *   **System Prompt:** A textarea to define a system-level instruction for the AI, influencing its responses.
    *   **Temperature Control:** A slider (0.0 to 2.0, step 0.1) to adjust the randomness of the AI's output.
    *   **Max Output Tokens:** An input field (100 to 8192) to set the maximum length of the AI's response.
    *   **Persistence:** All settings are automatically saved to and loaded from `localStorage`.

2.  **Chat Management:**
    *   **Clear Chat:** A button to clear the entire chat history after a confirmation prompt.
    *   **Export Chat:** A button to download the current chat history as a JSON file.
    *   **Message Counter:** Displays the total number of messages in the current chat session.

3.  **Message Enhancements:**
    *   **Timestamps:** Each message (user and bot) is displayed with a `HH:MM AM/PM` timestamp.
    *   **Copy Button:** A "Copy" button appears next to each AI message, allowing users to quickly copy its content to the clipboard.
    *   **Character Counter:** Shows the current character count and the maximum allowed (2000) for the user input.

4.  **API Integration Updates:**
    *   The chatbot uses the `gemini-1.5-flash-latest` model.
    *   The `systemPrompt` (if provided) is included in the `systemInstruction` field of the API request.
    *   `temperature` and `maxOutputTokens` from the settings panel are passed in the `generationConfig` of the API request.
    *   The API request body is structured as specified for the Google Gemini API.

5.  **Persistence:**
    *   **Chat History:** The entire chat history is saved to `localStorage` under the key `'chatHistory'`.
    *   **Chat Settings:** All settings (API Key, system prompt, temperature, max tokens, and settings panel state) are saved to `localStorage` under the key `'chatSettings'`.
    *   **Auto-Restore:** Both chat history and settings are automatically loaded and restored when the page is reloaded.

## Usage

1.  **Open `index.html`:** Load the `index.html` file in your web browser.
2.  **Enter API Key:** Expand the "Settings" panel and enter your Google Gemini API Key.
3.  **Configure Settings (Optional):** Adjust the system prompt, temperature, and max output tokens as desired. These settings will be saved automatically.
4.  **Start Chatting:** Type your message in the input area and click "Send" or press `Enter`.
5.  **Manage Chat:** Use the "Clear Chat" and "Export Chat" buttons to manage your conversation.
6.  **Copy AI Responses:** Click the "Copy" button next to any AI message to copy its text.

## License

This project is open-source and available under the MIT License.