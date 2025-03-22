# Speech Recognition Microservice (node.js) 

A microservice that translates audio to text and generates notes using Google Cloud Speech-to-Text API and OpenAI.

## Features

- Audio file upload and processing
- Speech-to-text conversion using Google Cloud Speech API
- Text processing with OpenAI
- CORS support for cross-origin requests
- File validation middleware
- Streaming audio processing

## Prerequisites

- Node.js (v14 or higher)
- Google Cloud Platform account with Speech-to-Text API enabled
- OpenAI API key

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd speachRecognition
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file in the root directory with the following variables:
```env
PORT=8080
GOOGLE_APPLICATION_CREDENTIALS=path/to/your/SpeechClient.json
OPENAI_API_KEY=your_openai_api_key
```

## Project Structure

```
src/
├── CORS/
│   └── config.js         # CORS configuration
├── config/
│   └── SpeechClient.json # Google Cloud credentials
├── handlers/
│   ├── streamHandler.js  # Audio stream processing
│   ├── speechRecognize.js # Speech recognition logic
│   └── gptProcess.js     # OpenAI text processing
├── middleware/
│   ├── isFile.js        # File validation middleware
│   └── isAuth.js        # Authentication middleware
└── index.js             # Main application entry point
```

## API Endpoints

### POST /upload-audio

Upload and process audio files.

**Request:**
- Method: POST
- Content-Type: multipart/form-data
- Body: 
  - `voice`: Audio file

**Response:**
- Success: 200 OK with processed text
- Error: 400 Bad Request or 500 Internal Server Error

## Usage

1. Start the development server:
```bash
npm run dev
```

2. Start the production server:
```bash
npm start
```

The server will start on port 8080 (or the port specified in your .env file).

## Dependencies

- @google-cloud/speech: ^6.5.0
- dotenv: ^16.4.5
- express: ^4.19.2
- multer: ^1.4.5-lts.1
- openai: ^4.40.0

## Security Notes

- Keep your `.env` file secure and never commit it to version control
- Ensure your Google Cloud credentials are properly secured
- The service includes CORS configuration for secure cross-origin requests
- File validation middleware is implemented to ensure proper file uploads

## License


ISC

## Author

Bohdan Kukhar 
