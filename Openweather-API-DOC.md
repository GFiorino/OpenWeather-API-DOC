# OpenWeather Current Weather Data API Documentation

## Overview
The OpenWeather Current Weather Data API gives you real-time weather information for any location worldwide. Whether you're building a weather widget, a forecasting tool, or need weather data for analysis, this API is your go-to resource for staying up-to-date with current conditions.

### Base URL
`https://api.openweathermap.org/data/2.5/weather`

## Authentication
To get started, you'll need to sign up and grab an API key from [OpenWeatherMap](https://home.openweathermap.org/users/sign_up). Make sure to include this key (`appid`) in all your API requests.

## Endpoint
### 1. Get Current Weather Data
**URL**: `GET /data/2.5/weather`

**Description**: Use this endpoint to get the current weather for a specific location by providing its latitude and longitude.

**Parameters**:
- **`lat`** (required): Latitude of the location. If you need to convert city names or zip codes to coordinates, try the Geocoding API.
- **`lon`** (required): Longitude of the location. Use the Geocoding API for conversions.
- **`appid`** (required): Your unique API key for authentication, available in your OpenWeather account.
- **`mode`** (optional): Response format. Options include `json` (default), `xml`, or `html`.
- **`units`** (optional): Units for temperature and other values. Use `standard` (Kelvin), `metric` (Celsius), or `imperial` (Fahrenheit). Default is `standard`.
- **`lang`** (optional): Set the response language (e.g., `lang=en` for English).

**Example Request**:
```plaintext
GET https://api.openweathermap.org/data/2.5/weather?lat=44.34&lon=10.99&appid=YOUR_API_KEY
```

**Example Response**:
```json
{
  "coord": {
    "lon": 10.99,
    "lat": 44.34
  },
  "weather": [
    {
      "id": 501,
      "main": "Rain",
      "description": "moderate rain",
      "icon": "10d"
    }
  ],
  "base": "stations",
  "main": {
    "temp": 298.48,
    "feels_like": 298.74,
    "temp_min": 297.56,
    "temp_max": 300.05,
    "pressure": 1015,
    "humidity": 64,
    "sea_level": 1015,
    "grnd_level": 933
  },
  "visibility": 10000,
  "wind": {
    "speed": 0.62,
    "deg": 349,
    "gust": 1.18
  },
  "rain": {
    "1h": 3.16
  },
  "clouds": {
    "all": 100
  },
  "dt": 1661870592,
  "sys": {
    "type": 2,
    "id": 2075663,
    "country": "IT",
    "sunrise": 1661834187,
    "sunset": 1661882248
  },
  "timezone": 7200,
  "id": 3163858,
  "name": "Zocca",
  "cod": 200
}
```

## Response Fields
- **`coord`**:
  - **`lon`**: Longitude of the location.
  - **`lat`**: Latitude of the location.
- **`weather`**: Weather conditions.
  - **`id`**: Weather condition ID.
  - **`main`**: Group of weather parameters (e.g., Rain, Snow, Clouds).
  - **`description`**: Detailed weather description.
  - **`icon`**: Weather icon ID.
- **`main`**: Main weather data.
  - **`temp`**: Current temperature. Default is in Kelvin, but can be Celsius/Fahrenheit if `units` is specified.
  - **`feels_like`**: Perceived temperature.
  - **`temp_min`**: Minimum temperature at the moment.
  - **`temp_max`**: Maximum temperature at the moment.
  - **`pressure`**: Atmospheric pressure (hPa).
  - **`humidity`**: Humidity percentage.
  - **`sea_level`**: Atmospheric pressure at sea level (hPa).
  - **`grnd_level`**: Atmospheric pressure at ground level (hPa).
- **`visibility`**: Visibility in meters (up to 10 km).
- **`wind`**: Wind information.
  - **`speed`**: Wind speed (default in meter/sec).
  - **`deg`**: Wind direction in degrees.
  - **`gust`**: Wind gust speed.
- **`clouds`**:
  - **`all`**: Cloudiness percentage.
- **`rain`**: Rain volume.
  - **`1h`**: Precipitation volume for the last hour (in mm).
- **`sys`**: System information.
  - **`country`**: Country code (e.g., IT for Italy).
  - **`sunrise`**: Sunrise time (Unix timestamp).
  - **`sunset`**: Sunset time (Unix timestamp).
- **`timezone`**: Timezone offset from UTC (seconds).
- **`name`**: Name of the city.
- **`cod`**: HTTP status code.

## Error Handling
The API returns standard HTTP status codes to indicate success or failure:
- **`401 Unauthorized`**: Invalid or missing API key.
- **`404 Not Found`**: Requested resource not found (e.g., invalid city name).
- **`500 Internal Server Error`**: Unexpected server issue.

**Example Error Response**:
```json
{
  "cod": 404,
  "message": "city not found"
}
```

## Rate Limiting
The OpenWeatherMap API uses rate limits to ensure fair usage. If you exceed your rate limit, you will receive a `429 Too Many Requests` response. Check your account plan for specific limits.

## Notes
- To improve accuracy, use the **Geocoding API** to convert city names or zip codes into precise latitude and longitude values.
- The **built-in geocoder** is deprecated. Please use the **Geocoding API** for all new projects.

## Contact and Support
If you need help, you can reach out to [OpenWeatherMap Support](https://openweathermap.org/support) or check the [OpenWeatherMap Documentation](https://openweathermap.org/api) for additional guidance.
