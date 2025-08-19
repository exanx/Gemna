# Gemna Chat

<p align="center">
  <img src="screenshots/ss instagram desktop.jpeg" alt="Instagram Desktop" width="48%">
  <img src="screenshots/ss whatsapp desktop.jpeg" alt="WhatsApp Desktop" width="48%">
</p>

<p align="center">
  <img src="screenshots/ss instagram mobile.png" alt="Instagram Mobile" width="30%">
  <img src="screenshots/ss whatsapp mobile.png" alt="WhatsApp Mobile" width="30%">
  <img src="screenshots/ss settings.png" alt="Settings" width="30%">
</p>

### A Customizable, Zero-Framework AI Chat Experience
****

**Gemna Chat** is a versatile and highly customizable AI chat web application designed for privacy, flexibility, and a beautiful user experience. Built entirely with vanilla JavaScript, HTML, and Tailwind CSS (via CDN), this project demonstrates that powerful, modern web apps don't always require heavy frameworks or complex build steps.

It's designed to be your personal chat interface, allowing you to create unique AI characters, style the conversation to your liking, and connect to multiple powerful large language models.

[**➡️ View the Live Demo**](https://exanx.github.io/gemna/) 

---

## ✨ Key Features

*   **🎨 Highly Themeable Interface:** Don't just chat, do it in style.
    *   **Pre-built Themes:** Instantly switch between popular messaging app styles like iMessage, WhatsApp, Messenger, Instagram, and X (Twitter).
    *   **Dark & Light Modes:** Automatically adapts to your system preference or can be toggled manually.
    *   **UI Toggles:** Customize your view by showing or hiding chat avatars and message timestamps.

*   **🤖 Multi-API & Multi-Model Support:** You're not locked into one ecosystem.
    *   **Google Gemini:** Connect directly to the Gemini API, with support for models like Gemini 1.5 Flash and Pro.
    *   **Groq:** Experience blazing-fast inference speeds by connecting to the Groq API, with support for models like Llama3 and Mixtral.
    *   **OpenRouter:** Access a massive variety of models from different providers (OpenAI, Anthropic, Mistral, and more) through a single API key.
    *   **Custom Model Support:** Easily add and use custom model strings for providers that support it.

*   **🎭 Advanced Character Creation:** Craft the perfect AI chat partner.
    *   **AI Personas:** Define a character's personality, background, and even their specific texting style.
    *   **User Personas:** Define your own role in the conversation to create more immersive roleplaying or contextual interactions.
    *   **Group Chats:** Create group conversations with multiple AI characters, who can interact with each other and the user.

*   **🚀 AI-Powered Enhancements (Gemini Required):**
    *   **Enhance Persona:** Start with a simple idea and let the AI flesh out a detailed character profile for you.
    *   **Generate Image Prompts:** Automatically create detailed, consistent image generation prompts based on a character's persona.
    *   **Analyze Avatars:** Upload an avatar and let the AI analyze it to generate a name and starting persona.
    *   **Image Generation & TTS:** Generate images directly in chat and have messages read aloud using Gemini's text-to-speech capabilities.

*   **🔒 Privacy-First Architecture:**
    *   **Client-Side E2EE:** All chat messages are encrypted **on your device** using AES before being sent to the cloud (however, persona descriptions aren't being encrypted currently). The encryption key is also generated on your device and never leaves your control.
    *   **Local-First by Default:** The app works perfectly without an account, storing all data securely in your browser's local storage.
    *   **Optional Cloud Sync:** Sign in (Anonymously or with Google) to securely sync your encrypted data across devices using Firebase. **We never see your unencrypted conversations.**

*   **📦 Zero-Dependency & Portable:**
    *   **No Build Step:** No `npm install`, no `webpack`, no compilers. Just clone the repository and open `index.html`.
    *   **Data Portability:** Easily import and export your characters and their entire chat history as a single `.json` file.

## 🛠️ Tech Stack

*   **Frontend:**
    *   **HTML5 & CSS3**
    *   **Vanilla JavaScript (ES6+):** No frameworks, no libraries, just modern JS.
    *   **Tailwind CSS (via CDN):** For rapid, utility-first styling.
    *   **Lucide Icons:** For a clean and beautiful icon set.
    *   **Marked.js:** For rendering Markdown in chat bubbles.
    *   **CryptoJS:** For client-side AES encryption.
*   **Backend & Data Persistence:**
    *   **Browser Local Storage:** The default, offline-first storage mechanism.
    *   **Firebase (Optional):**
        *   **Authentication:** For Google & Anonymous sign-in.
        *   **Firestore:** For secure, real-time cloud storage of encrypted data.

## 🚀 Getting Started

You can run Gemna Chat locally with just a few steps. Setting up Firebase is optional but recommended for cloud sync.

### 1. Set Up a Firebase Project (Optional)

If you want to enable cloud sync and user accounts:

1.  Go to the [Firebase Console](https://console.firebase.google.com/) and create a new project.
2.  In your project, go to the **Authentication** section, click "Get Started," and enable the **Google** and **Anonymous** sign-in providers.
3.  Go to the **Firestore Database** section, click "Create database," and start in **Production mode**. Choose a location close to you.
4.  Navigate to the **Rules** tab in Firestore and replace the default rules with the following:
    ```
    rules_version = '2';
    service cloud.firestore {
      match /databases/{database}/documents {
        // Users can only read/write their own data in their own subdirectory
        match /users/{userId}/{document=**} {
          allow read, write: if request.auth != null && request.auth.uid == userId;
        }
      }
    }
    ```
5.  Go to your Project Settings (click the ⚙️ icon) and in the "General" tab, scroll down to "Your apps."
6.  Click the Web icon (`</>`) to add a new web app. Give it a nickname and click "Register app."
7.  Firebase will provide you with a `firebaseConfig` object. **Copy this entire object.**

### 2. Set Up the Application Locally

1.  Clone the repository:
    ```bash
    git clone https://github.com/your-username/gemna-chat.git
    cd gemna-chat
    ```
2.  Open the `index.html` file in your code editor.
3.  Find the `<script type="module">` tag at the bottom of the file.
4.  Locate the `firebaseConfig` constant and **replace the placeholder object with the one you copied from your Firebase project.**
    ```javascript
    // Your provided Firebase configuration
    const firebaseConfig = { // PASTE YOUR CONFIG OBJECT HERE
        apiKey: "...",
        authDomain: "...",
        projectId: "...",
        // ...and so on
    };
    ```
5.  **That's it!** Simply open the `index.html` file in your web browser to start using the app.

### 3. Configure API Keys

To chat with an AI, you need to provide an API key:

1.  Open the app and click the Settings icon (⚙️) in the top-right corner.
2.  Navigate to the "API & Model" section.
3.  Select your desired API Provider (Gemini, Groq, or OpenRouter).
4.  Enter your API key. You can get them here:
    *   [**Google AI Studio**](https://aistudio.google.com/app/apikey) for Gemini
    *   [**GroqCloud Console**](https://console.groq.com/keys) for Groq
    *   [**OpenRouter Keys**](https://openrouter.ai/keys) for OpenRouter

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/your-username/gemna-chat/issues).

1.  Fork the Project
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4.  Push to the Branch (`git push origin feature/AmazingFeature`)
5.  Open a Pull Request

## 📄 License

This project is distributed under the MIT License. See `LICENSE` for more information.
