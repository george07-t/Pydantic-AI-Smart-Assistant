# Smart Assistant with Tools

This project implements a smart assistant using the `pydantic-ai` library. The assistant is capable of performing various tasks such as fetching weather information, evaluating mathematical expressions, planning trips, managing Google Calendar events, retrieving upcoming events, and performing web searches. The assistant is integrated with Gradio to provide a user-friendly chatbot interface.

---

## Features

### 1. **Weather Information**
- Fetches the current weather for a specified city using the WeatherAPI.
- Example: "What's the weather in Dhaka?"

### 2. **Mathematical Expression Evaluation**
- Evaluates mathematical expressions provided by the user.
- Example: "What is 2 + 3 * 4?"

### 3. **Trip Planning**
- Plans a trip by providing details such as attractions, food recommendations, activities, and budget.
- Example: "Plan a 5-day trip to Paris."

### 4. **Google Calendar Integration**
- Performs intelligent web searches to retrieve relevant information quickly and efficiently.
- Example: "Add a trip to Sylhet from June 1 to June 5."

### 5. **Google Smart Web Search Integration**
- Adds events to Google Calendar.
- Retrieves upcoming events from Google Calendar within a specified date range.
- Example: "what is the Current status of Bangladesh?"


### 5. **Chatbot Interface**
- A Gradio-based chatbot interface for interacting with the assistant.

---

## Usage

### 1. **Environment Setup**
- Install the required dependencies:
  ```bash
  pip install pydantic-ai ollama logfire devtools --upgrade google-api-python-client google-auth-httplib2 google-auth-oauthlib
  ```
- Create a `.env` file in the project directory and add your WeatherAPI key:
  ```bash
  weatherapicom_API_KEY=your-weather-api-key
  ```
- Ensure you have a `credentials.json` file for Google Calendar API authentication.

### 2. **Run the Assistant**
- Launch the assistant by running the notebook or script. The Gradio interface will open in your browser.

## Tools and Functions

### 1. **Weather Tool**
- **Function**: `get_weather`
- **Description**: Fetches the current weather temperature for a specified city using the WeatherAPI.
- **API Used**: WeatherAPI
- **Example**:
  ```python
  await get_weather(context, "Dhaka")
  ```
### 2. **Math Expression Tool**
- **Function**: `calculate_expression`
- **Description**: Evaluates mathematical expressions provided as a string.
- **Example**:
  ```python
  await calculate_expression("2 + 3 * 4")
  ```
### 3. **Trip Planner Tool**
- **Function**: `tripPlanner`
- **Description**: Plans a trip by providing details such as attractions, food recommendations, activities, and budget.
- **Example**:
  ```python
  await tripPlanner("2024-06-01", "2024-06-05", "Paris")
  ```
### 4. **Google Calendar Tools**
##### Add Event
- **Function**: `add_to_google_calendar`
- **Description**: Adds an event to Google Calendar with the provided details.
- **Example**:
  ```python
  await add_to_google_calendar("Trip to Sylhet", "Sylhet", "2024-06-01", "2024-06-05")
  ```
##### Upcoming Events
- **Function**: `get_upcoming_events`
- **Description**: Retrieves upcoming Google Calendar events within a given date range or defaults to the next month.
- **Example**:
  ```python
  await get_upcoming_events("2024-06-01", "2024-06-15")
  ```
### 5. **Google Web Search Tool**
- **Function**: `searchWeb`
- **Description**: Searches for a query using Google Search and returns the top 5 results with titles and descriptions.
- **Example**:
  ```python
  await searchWeb(What is the Current Status of Bangladesh?)
  ```

## Gradio Interface

The assistant is integrated with Gradio to provide a chatbot interface. Users can:
- **Ask questions or give commands** in the text box.
- **View the assistant's responses** in the chat window.
- **Clear the chat history** using the "Clear Chat" button.

---

## How It Works

### Agent Setup
- The assistant uses the `pydantic-ai` library to define tools and manage interactions.
- Tools are registered with the agent to handle specific tasks.

### Dependency Injection
- Dependencies like the WeatherAPI key and HTTP client are injected into the agent.

### Tool Execution
- The agent decides which tool to call based on the user's input.
- Tools are executed asynchronously, and their results are returned to the user.

### Gradio Integration
- The chatbot interface is built using Gradio.
- User inputs are processed, and the assistant's responses are displayed in real-time.

---

## Example Usage

### Fetch Weather
- **Input**: "What's the weather in Dhaka?"
- **Output**: "The weather in Dhaka is 30°C."

### Evaluate Expression
- **Input**: "What is 10 / 2?"
- **Output**: "5.0"

### Plan a Trip
- **Input**: "Plan a 3-day trip to Tokyo."
- **Output**: Details about attractions, food, activities, and budget.

### Add Event to Calendar
- **Input**: "Add a trip to Sylhet from June 1 to June 5."
- **Output**: "✅ Trip added to your Google Calendar: [Event Link]"

### Get Upcoming Events
- **Input**: "What are my events for the next week?"
- **Output**: List of upcoming events with dates and summaries.

### Web Search
- **Input**: "What is the status of Bangladesh now?"
- **Output**: List of search links with their title and descriptions.

---

## Notes
- Ensure that the required API keys are set up in the `.env` file.
- Google Calendar integration requires `credentials.json` for authentication.
- The assistant uses `pydantic-ai` for structured output and tool management.

---

## License
This project is licensed under the MIT License. See the [MIT LICENSE](./LICENSE) file for details.
