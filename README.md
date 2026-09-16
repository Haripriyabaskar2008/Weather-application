# AI Weather Assistant

An AI-powered conversational weather application that provides real-time weather information for cities around the world. The application combines a Large Language Model (LLM), function calling, and the Open-Meteo Weather API to understand natural-language weather queries and retrieve current weather data.
 LIVE DEMONSTRATION AND APP LINK:
 http://localhost:8501/
 <img width="742" height="369" alt="APPLICATION1" src="https://github.com/user-attachments/assets/1a2739c9-c502-455e-8872-e419eae0c926" />
<img width="562" height="285" alt="APPLICATION2" src="https://github.com/user-attachments/assets/3641038f-1f3f-4272-8fa6-5368dd62d445" />

## Features

* Conversational AI-based weather assistant
* Real-time weather information for cities worldwide
* Temperature, humidity, and wind speed information
* LLM Function Calling for weather-related queries
* Automatic city identification from natural-language questions
* Interactive chat interface using Streamlit
* Real-time data retrieval through Open-Meteo APIs
* Secure API key management using environment variables
* Error handling for invalid cities and API failures

## Technologies Used

| Technology                | Purpose                          |
| ------------------------- | -------------------------------- |
| Python                    | Application development          |
| Streamlit                 | Web application interface        |
| Hugging Face              | LLM integration                  |
| Qwen/Qwen2.5-72B-Instruct | Language model                   |
| Open-Meteo                | Weather data                     |
| Open-Meteo Geocoding API  | City and location identification |
| Requests                  | HTTP/API communication           |
| python-dotenv             | Environment variable management  |

## AI Model

The application uses the following Hugging Face model:

```text
Qwen/Qwen2.5-72B-Instruct
```

The model is integrated using the Hugging Face `InferenceClient`.

The LLM processes the user's natural-language query and determines when the `get_weather` function should be called to retrieve real-time weather information.

## System Workflow

```text
User Query
    |
    v
Hugging Face LLM
    |
    v
Function Calling
    |
    v
get_weather(city)
    |
    v
Open-Meteo Geocoding API
    |
    v
Latitude and Longitude
    |
    v
Open-Meteo Weather API
    |
    v
Current Weather Data
    |
    v
LLM Response
    |
    v
Streamlit User Interface
```

## Project Structure

```text
AI-Weather-Application/
|
├── Weather app.py
├── Weather requirements.txt
├── README.md
├── .gitignore
└── .env
```

### Environment File

The `.env` file is used locally to store the Hugging Face API token.

```text
HF_TOKEN=your_huggingface_token
```

The `.env` file must not be uploaded to GitHub.

The `.gitignore` file should contain:

```text
.env
__pycache__/
*.pyc
.venv/
venv/
```

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/AI-Weather-Application.git
```

Navigate to the project directory:

```bash
cd AI-Weather-Application
```

### 2. Install Dependencies

Install the required Python packages:

```bash
py -m pip install -r "Weather requirements.txt"
```

The main dependencies include:

```text
streamlit
requests
python-dotenv
huggingface-hub
```

### 3. Configure the Environment

Create a `.env` file in the project root directory:

```text
HF_TOKEN=your_huggingface_token
```

Replace `your_huggingface_token` with a valid Hugging Face access token.

Do not commit the `.env` file to the repository.

## Running the Application

Start the Streamlit application using:

```bash
py -m streamlit run "Weather app.py"
```

The application will normally be available at:

```text
http://localhost:8501
```

Open this address in a web browser to access the application.

For Google Chrome on Windows:

```powershell
start chrome http://localhost:8501
```

For Microsoft Edge:

```powershell
start msedge http://localhost:8501
```

## Example Queries

Users can interact with the application using natural-language questions such as:

```text
What's the weather in Chennai?
```

```text
Tell me the temperature in Mumbai.
```

```text
What is the humidity in Delhi?
```

```text
How windy is it in Bengaluru?
```

```text
Give me the current weather in London.
```

The application identifies the requested city and retrieves the corresponding current weather information.

## Weather Information

The application provides the following information:

* Temperature
* Relative humidity
* Wind speed
* City
* Country

Example response:

```text
Temperature: 30 °C
Humidity: 72%
Wind Speed: 14 km/h

Location: Chennai, India
```

## LLM Function Calling

Function calling is a key component of this application.

The LLM is provided with a weather tool named:

```text
get_weather(city)
```

When a user asks a weather-related question, the model determines whether the function is required.

For example:

```text
User:
What's the weather in Chennai?

        |
        v

LLM:
get_weather("Chennai")

        |
        v

Open-Meteo API:
Current weather data

        |
        v

LLM:
Natural-language response
```

This approach allows the application to combine natural-language understanding with real-time external data.

## API Integration

### Open-Meteo Geocoding API

The Geocoding API is used to identify a city and obtain its geographical coordinates.

```text
https://geocoding-api.open-meteo.com/v1/search
```

### Open-Meteo Forecast API

The Forecast API is used to retrieve current weather information based on latitude and longitude.

```text
https://api.open-meteo.com/v1/forecast
```

The application uses the following current weather parameters:

```text
Temperature
Relative Humidity
Wind Speed
```

## Error Handling

The application handles several possible errors, including:

* Invalid or unavailable city names
* Weather API request failures
* Network-related errors
* Unexpected application errors
* Missing Hugging Face API token

If the Hugging Face token is not configured, the application displays an appropriate configuration message and stops execution.

## Security

Sensitive credentials are stored using environment variables rather than being hard-coded into the application.

The Hugging Face API token is loaded using:

```python
from dotenv import load_dotenv
import os

load_dotenv()

HF_TOKEN = os.getenv("HF_TOKEN")
```

The `.env` file is excluded from Git tracking through `.gitignore`.

Never publish API tokens, passwords, or other sensitive credentials in a public GitHub repository.

## Future Enhancements

The application can be extended with the following features:

* Multi-day weather forecasts
* Rain probability
* Weather condition descriptions
* Feels-like temperature
* Sunrise and sunset information
* Weather trend visualizations
* Automatic location-based weather
* Interactive weather maps
* Severe weather alerts
* Multi-language support
* Improved mobile responsiveness

## Learning Outcomes

This project demonstrates practical implementation of:

* Python programming
* REST API integration
* Large Language Model integration
* LLM Function Calling
* Natural Language Processing
* JSON data handling
* Environment variable management
* Streamlit application development
* API error handling
* Git and GitHub project management

## Author

**HARI PRIYA.B**

B.Sc. Computer Science with Artificial Intelligence

### Areas of Interest

* Artificial Intelligence
* Machine Learning
* Python
* Data Analytics
* AI Application Development
* Space Technology

## License

This project is developed for educational and learning purposes.
