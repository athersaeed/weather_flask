# Weather App

A simple Flask application that uses the [OpenWeatherMap API](https://openweathermap.org/) to retrieve current weather conditions for a given city. The application allows users to enter a city name and displays the temperature, weather status, and "feels like" temperature in Celsius.

---

## Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
  - [Running the App](#running-the-app)
  - [Accessing the App](#accessing-the-app)
- [Project Structure](#project-structure)
- [Important Files](#important-files)
- [License](#license)

---

## Features

- **City-based Weather Data**: Users can enter a city name to get the current temperature, weather description, and "feels like" temperature.
- **Default City**: If no city is entered, the default city is set to Toronto.
- **Error Handling**: Displays a "City Not Found" page if the city cannot be found using OpenWeatherMap.
- **Responsive HTML templates**: Basic HTML structure with a simple CSS file for styles.

---

## Prerequisites

1. **Python 3.7+**: Make sure you have Python 3.7 or higher installed.
2. **Pip**: Use the latest version of pip to install the required packages.
3. **OpenWeatherMap API Key**: Sign up for a free account at [OpenWeatherMap](https://openweathermap.org/), and obtain an API key.

---

## Installation

1. **Clone the repository** or download the source code:

    ```bash
    git clone https://github.com/your-username/weather-app.git
    cd weather-app
    ```

2. **Create a virtual environment (optional but recommended)**:

    ```bash
    python -m venv venv
    source venv/bin/activate       # On macOS/Linux
    venv\Scripts\activate          # On Windows
    ```

3. **Install required dependencies**:

    ```bash
    pip install -r requirements.txt
    ```

4. **Create a `.env` file** in the root directory of the project and add your OpenWeatherMap API key:

    ```
    API_KEY=your_openweathermap_api_key
    ```

---

### Running the App

Use the following command to start the app with Waitress:

```bash
python server.py
```
The console will show that Waitress has started serving on `http://0.0.0.0:8000`.

---
## Accessing the App
Open your brownser and go to:
```bash
http://localhost:8000
```
- You will see a home page with a form to enter a city name.
- Submitting the form sends a request to /weather and retrieves the current weather for the specified city.
- If the city is invalid or not found, the app will display an error page letting you try again.
---
## Project Structure
```bash
.
├── .env                  # Stores environment variables (API key)
├── city-not-found.html   # Rendered when the city is not found
├── index.html            # Home page template
├── requirements.txt      # Project dependencies
├── server.py             # Flask app using Waitress for serving
├── static
│   └── styles
│       └── style.css     # Styling for HTML templates
├── weather.html          # Rendered with weather data
└── weather.py            # Fetches weather data from OpenWeatherMap API
```
---
## Important Files
1. `weather.py`
    - Contains the function `get_current_weather(city='Toronto')`.
    - Makes a request to the OpenWeatherMap API using the API key in the `.env` file.
    - Returns a JSON response with the city’s current weather data.
2. `server.py`
    - Sets up a Flask application and routes:
        - `/` or `/index`: Renders `index.html`
        - `/weather`: Accepts city name via query string and uses `get_current_weather` to fetch data. Renders `weather.html` on success or `city-not-found.html` on failure.
    - Uses **Waitress** to serve the app on host `0.0.0.0` and port `8000`
3. **HTML Templates**
    - `index.html`: Home page with a form for entering a city.
    - `weather.html`: Displays the weather data.
    - `city-not-found.html`: Shown if a city is invalid or not found.
4. `style.css` (in `static/styles/`):
    - Basic styling for the HTML templates
---
