# AI Email Writer ✉️

An AI-powered email reply generator built with **React** and **Spring Boot**. The application takes the content of an incoming email, optionally applies a preferred tone, and uses the **Google Gemini API** to generate a reply. Users can review the generated response and copy it to the clipboard.

## 🚀 Features

- Generate email replies from original email content.
- Choose an optional tone: Professional, Casual, or Friendly.
- Display generated replies in the frontend.
- Copy generated replies to the clipboard.
- Securely configure Gemini API credentials using environment variables.

## 🛠️ Tech Stack

**Frontend**
- React 19
- Vite
- Material UI (MUI)
- Axios

**Backend**
- Java 21
- Spring Boot 4.1.1
- Spring Web MVC
- Spring WebFlux (WebClient)
- Maven
- Lombok

**AI Integration**
- Google Gemini API

## 📁 Project Structure

```text
Project/
├── EmailWriter/                  
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/email/EmailWriter/
│   │   │   │   ├── EmailWriterApplication.java
│   │   │   │   └── app/
│   │   │   │       ├── EmailGeneratorController.java
│   │   │   │       ├── EmailGeneratorService.java
│   │   │   │       ├── EmailRequest.java
│   │   │   │       └── WebClientConfig.java
│   │   │   └── resources/
│   │   │       └── application.properties
│   │   └── test/
│   ├── pom.xml
│   └── mvnw
│
├── email-writer-react/
│   ├── public/
│   ├── src/
│   │   ├── assets/
│   │   ├── App.jsx
│   │   ├── App.css
│   │   ├── index.css
│   │   └── main.jsx
│   ├── package.json
│   └── vite.config.js
│
└── README.md
```

## ⚙️ How It Works

1. User enters the original email content.
2. User selects an optional email tone.
3. React sends a POST request to the Spring Boot backend.
4. Spring Boot generates a prompt and communicates with Google Gemini API using WebClient.
5. Gemini generates the email reply.
6. Backend extracts the generated response and returns it to React.
7. User can view and copy the generated reply.

## 🔗 API Documentation

### Generate Email Reply

**Endpoint:** `POST /api/email/generate`

**Base URL:** `http://localhost:8080`

**Request Body:**

```json
{
  "emailContent": "Hello, I wanted to follow up regarding the project update.",
  "tone": "professional"
}
```

**Supported tones:**
- professional
- casual
- friendly

The tone field is optional.

**Response:** Plain text containing the generated email reply.

## 📋 Prerequisites

- Java JDK 21 or later
- Node.js and npm
- Maven
- Google Gemini API key

## 💻 Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
cd YOUR_REPOSITORY
```

### 2. Configure Gemini API

The backend uses environment variables:

```properties
gemini.api.url=${GEMINI_URL}
gemini.api.key=${GEMINI_KEY}
```

Set your environment variables:

```bash
export GEMINI_URL="YOUR_GEMINI_API_ENDPOINT_URL"
export GEMINI_KEY="YOUR_GEMINI_API_KEY"
```

Never upload your actual API key to GitHub.

### 3. Start the Spring Boot backend

```bash
cd EmailWriter
./mvnw spring-boot:run
```

Backend runs on:

`http://localhost:8080`

### 4. Start the React frontend

Open another terminal:

```bash
cd email-writer-react
npm install
npm run dev
```

Open the URL provided by Vite, usually:

`http://localhost:5173`

**Note:** The frontend currently sends requests to `http://localhost:8080/api/email/generate`.

## 🏗️ Build Commands

Frontend:

```bash
cd email-writer-react
npm run build
```

Backend:

```bash
cd EmailWriter
./mvnw clean package
```

## 🔐 Security Notes

- Keep your Gemini API key private.
- Never expose API keys in frontend code.
- Restrict CORS origins before production deployment.
- Configure the frontend API URL for the production backend.
- Always review AI-generated replies before sending them.

## 🔮 Future Improvements

- Add input validation.
- Improve error handling.
- Add email templates.
- Support multiple writing styles.
- Add authentication and user management.
- Deploy frontend and backend.

## 👨‍💻 Author

**Alok Kumar Sah**

---

⭐ If you find this project useful, consider giving it a star!
