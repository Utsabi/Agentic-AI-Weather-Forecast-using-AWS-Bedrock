# 🌦️ Agentic Weather Assistant using Amazon Bedrock

Our Weather Agent intelligently retrieves real-time forecasts from the
National Weather Service (NWS) using an agentic AI architecture powered
by Amazon Bedrock and Claude Sonnet.

------------------------------------------------------------------------

## 🚀 Our Agent's Solution

Our weather agent:

-   Understands user location (city, ZIP code, coordinates, informal
    input)
-   Maps input to correct latitude/longitude
-   Generates proper National Weather Service API calls
-   Fetches real-time weather forecast data
-   Processes complex JSON into readable summaries
-   Presents results in a user-friendly format

------------------------------------------------------------------------

# 🧠 Why Amazon Bedrock for Agentic AI?

Amazon Bedrock provides the perfect foundation for agentic systems:

-   **Multiple AI Models** -- Access Claude, Nova, Llama, and other
    leading foundation models.
-   **Managed Infrastructure** -- No servers to manage.
-   **Enterprise Security** -- Built-in compliance and data protection.
-   **Easy Integration** -- Works seamlessly with other AWS services.
-   **Cost Effective** -- Pay only for what you use.

------------------------------------------------------------------------

## 🤖 Why Claude Sonnet?

Claude Sonnet specifically excels at:

-   Complex reasoning and planning\
-   Processing structured data\
-   Generating human-like responses

------------------------------------------------------------------------

# 🌐 National Weather Service (NWS) API Overview

The NWS provides free weather data through a **two-step API process**.

## 1️⃣ Points API

    https://api.weather.gov/points/{lat},{lon}

-   Takes latitude/longitude as input
-   Returns which NWS forecast office covers that location
-   Provides grid coordinates for that location

Example:\
Seattle (47.6062, -122.3321) → SEW office, grid 124,67

------------------------------------------------------------------------

## 2️⃣ Forecast API

    https://api.weather.gov/gridpoints/{office}/{gridX},{gridY}/forecast

-   Uses office + grid coordinates from Points API
-   Returns detailed weather forecast data in JSON format

------------------------------------------------------------------------

## ❓ Why Two APIs?

The NWS divides the U.S. into forecast grids.\
The Points API identifies the correct grid.\
The Forecast API retrieves the actual weather data.

------------------------------------------------------------------------

# 🔄 How Our Weather Agent Works

User Input → AI Planning → API Calls → AI Summary → Response

------------------------------------------------------------------------

## 👤 Step 1: User Input

Supported formats:

-   City names ("Seattle", "Seattle, WA")
-   ZIP codes ("90210")
-   Informal descriptions ("downtown Portland")
-   Coordinates ("47.6062, -122.3321")

------------------------------------------------------------------------

## 🧠 Step 2: AI Planning

Claude:

-   Determines coordinates
-   Identifies NWS endpoints
-   Plans API call sequence

------------------------------------------------------------------------

## 🔗 Step 3: API Calls

**Points API**

    https://api.weather.gov/points/{lat},{lon}

**Forecast API**

    https://api.weather.gov/gridpoints/{office}/{gridX},{gridY}/forecast

------------------------------------------------------------------------

## 📊 Step 4: AI Summary

Raw JSON → Human-friendly summary

Example output:

    Today: Partly cloudy with a high of 72°F
    Wind: West at 5–10 mph

------------------------------------------------------------------------

# 🤖 What Makes This Truly Agentic?

### ❌ Traditional (Hardcoded)

``` python
if location == "Seattle":
    api_url = "https://api.weather.gov/gridpoints/SEW/124,67/forecast"
```

### ✅ Agentic (Dynamic Reasoning)

``` python
ai_prompt = f"Generate NWS API calls for: {location}"
api_urls = claude_4_sonnet(ai_prompt)
```

The AI reasons, plans, adapts, and executes dynamically.

------------------------------------------------------------------------

# 🛠️ Running the Project

## CLI Version

    python weather_agent_cli.py

## Web Version (Streamlit)

    streamlit run weather_agent_web.py

------------------------------------------------------------------------

# 📌 Summary

This project demonstrates how to build a real-world Agentic AI system
using:

-   Amazon Bedrock
-   Claude Sonnet
-   National Weather Service APIs
-   Dynamic reasoning & planning
