# Text Emotion Analyzer

A Flask-based web application that uses IBM Watson NLP services to detect and analyze emotions in text. This application identifies five core emotions (anger, disgust, fear, joy, and sadness) and determines the dominant emotion in any given text input.

## Features

- **Real-time Emotion Analysis**: Analyze text in real-time through a user-friendly web interface
- **Multi-Emotion Detection**: Detects and scores five emotions:
  - Anger
  - Disgust
  - Fear
  - Joy
  - Sadness
- **Dominant Emotion Identification**: Automatically identifies which emotion is most prevalent in the text
- **Error Handling**: Gracefully handles invalid inputs and API errors
- **REST API**: Backend API endpoint for emotion detection
- **Responsive UI**: Bootstrap-based frontend for a clean user experience

## Project Structure

```
Text-Emotion-Analyzer/
├── EmotionDetection/
│   ├── __init__.py              # Package initialization
│   └── emotion_detection.py     # Core emotion detection logic
├── static/
│   └── mywebscript.js          # Frontend JavaScript for API calls
├── templates/
│   └── index.html              # Main web interface
├── server.py                    # Flask web server
├── test_emotion_detection.py   # Unit tests
├── .gitignore                  # Git ignore rules
├── LICENSE                     # Apache 2.0 License
└── README.md                   # This file
```

## Technologies Used

- **Python 3.x**: Core programming language
- **Flask**: Web framework for the application server
- **Watson NLP**: IBM Watson Natural Language Processing for emotion analysis
- **Bootstrap 4.3.1**: Frontend styling framework
- **unittest**: Python testing framework

## Installation

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd Text-Emotion-Analyzer
   ```

2. **Install required dependencies**:
   ```bash
   pip install flask requests
   ```

## Usage

### Running the Application

1. **Start the Flask server**:
   ```bash
   python server.py
   ```

2. **Access the application**:
   Open your web browser and navigate to:
   ```
   http://localhost:5000
   ```

3. **Analyze text**:
   - Enter any text in the input field
   - Click "Run Sentiment Analysis"
   - View the emotion scores and dominant emotion in the results section

### API Endpoint

The application exposes a REST API endpoint for programmatic access:

**Endpoint**: `/emotionDetector`

**Method**: GET

**Parameters**:
- `textToAnalyze` (string): The text to analyze for emotions

**Example Request**:
```
GET http://localhost:5000/emotionDetector?textToAnalyze=I am so happy today!
```

**Response Format**:
```
For the given statement, the system response is 'anger': 0.001, 'disgust': 0.002, 'fear': 0.003, 'joy': 0.95 and 'sadness': 0.01. The dominant emotion is joy.
```

**Error Response**:
```
Invalid text! Please try again!
```

## How It Works

1. **User Input**: User enters text through the web interface
2. **API Call**: JavaScript sends a GET request to the `/emotionDetector` endpoint
3. **Watson NLP Processing**: The backend calls IBM Watson NLP API with the text
4. **Emotion Analysis**: Watson analyzes the text and returns emotion scores
5. **Response Formatting**: The application formats the results and identifies the dominant emotion
6. **Display Results**: Results are displayed in the web interface

## Testing

The project includes comprehensive unit tests for emotion detection:

```bash
python test_emotion_detection.py
```

**Test Coverage**:
- Joy detection test
- Anger detection test
- Disgust detection test
- Sadness detection test
- Fear detection test

## API Details

### Watson NLP Emotion Detection

The application uses the Watson NLP Emotion Predict API:
- **Endpoint**: `https://sn-watson-emotion.labs.skills.network/v1/watson.runtime.nlp.v1/NlpService/EmotionPredict`
- **Model**: `emotion_aggregated-workflow_lang_en_stock`
- **Language**: English

### Error Handling

The application handles various error scenarios:
- **Empty or invalid text**: Returns error message
- **API errors (400 status)**: Returns all emotion values as `None`
- **Missing parameters**: Validates input before processing

## Development

### EmotionDetection Module

The `emotion_detection.py` module provides the core functionality:

```python
from EmotionDetection import emotion_detector

result = emotion_detector("I am happy!")
# Returns: {
#     'anger': 0.001,
#     'disgust': 0.002,
#     'fear': 0.003,
#     'joy': 0.95,
#     'sadness': 0.01,
#     'dominant_emotion': 'joy'
# }
```

### Adding New Features

To extend the application:
1. Modify `emotion_detection.py` for core logic changes
2. Update `server.py` for new endpoints or response formats
3. Enhance `index.html` and `mywebscript.js` for UI improvements
4. Add tests in `test_emotion_detection.py` for new functionality

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

Copyright 2020 IBM Developer Skills Network

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Acknowledgments

- IBM Watson for providing the NLP emotion detection API
- IBM Developer Skills Network for the initial project framework

## Support

For issues, questions, or contributions, please open an issue in the repository.

---

**Note**: This application requires an active internet connection to communicate with the Watson NLP API service.
