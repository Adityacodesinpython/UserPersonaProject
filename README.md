# Reddit User Persona Generator

This Python script fetches a Reddit user's posts and comments using the PRAW library, analyzes them with the Hugging Face Inference API, and generates a detailed user persona with citations. The persona includes fields like name, age, occupation, personality type, motivations, and more, saved to a text file.

## Prerequisites

- **Python 3.8+**: Ensure Python is installed on your system. Download from python.org.
- **pip**: Python's package manager, typically included with Python.
- A Reddit account to obtain API credentials.
- A Hugging Face account to obtain an API key.

## Setup Instructions

### Step 1: Install Required Libraries

Install the necessary Python packages using pip:

```bash
pip install praw huggingface_hub
```

- **PRAW**: Python Reddit API Wrapper for interacting with Reddit's API.
- **huggingface_hub**: For accessing the Hugging Face Inference API.

### Step 2: Obtain Reddit API Credentials

1. **Create a Reddit Account**: If you don't have one, sign up at reddit.com.

2. **Register an App**:

   - Go to reddit.com/prefs/apps.
   - Scroll to the bottom and click **Create an App**.
   - Fill in:
     - **Name**: Choose a name (e.g., "PersonaScraper").
     - **App Type**: Select "script".
     - **Description**: Optional.
     - **Redirect URI**: Use `http://localhost:8000`.
   - Click **Create App**.

3. **Retrieve Credentials**:

   - Note the **client_id** (below the app name).
   - Note the **client_secret** (keep this secure).
   - The **user_agent** is a custom string, e.g., "UserPersonaScraper" (unique identifier for your app).

4. **Update the Script**:

   - Open the script (`persona_generator.py` or your script name).

   - Replace the placeholder values in the Reddit API setup section:

     ```python
     os.environ['REDDIT_CLIENT_ID'] = "Your_Client_Id"
     os.environ['REDDIT_CLIENT_SECRET'] = "Your_Client_Secret"
     ```

   - Insert your `client_id` and `client_secret` from Reddit.

### Step 3: Obtain Hugging Face API Key

1. **Create a Hugging Face Account**: Sign up at huggingface.co.

2. **Generate an API Key**:

   - Go to your Hugging Face profile settings.
   - Click **Create new token**, give it a name, and select **Read** access.
   - Copy the API key.

3. **Update the Script**:

   - Replace the placeholder API key in the Hugging Face setup section:

     ```python
     os.environ['HUGGINGFACE_API_KEY'] = "Your_Api_Key"
     ```

   - Insert your Hugging Face API key.

### Step 4: File Setup

- Save the script as `persona_generator.py` (or another name of your choice).
- Ensure you have write permissions in the directory where the script runs, as it will create output files (`persona_u_<username>.txt`).

## Running the Script

1. **Open a Terminal or Command Prompt**:

   - Navigate to the directory containing the script:

     ```bash
     cd /path/to/script/directory
     ```

2. **Run the Script**:

   - Execute the script with Python:

     ```bash
     python persona_generator.py
     ```

3. **Provide Input**:

   - When prompted, enter a Reddit user profile URL (e.g., `https://www.reddit.com/user/example_user/`).
   - The script will:
     - Extract the username.
     - Fetch the user's recent posts and comments (up to 100 each).
     - Analyze the data using the Hugging Face Inference API with the Mistral-7B model.
     - Generate a detailed persona with citations.
     - Save the output to a file named `persona_u_<username>.txt`.

## Output

- The script creates a text file in the same directory, formatted as:

  ```
  👤 User Persona for u/<username>
  
  [Generated persona content with fields like Name, Age, Occupation, etc., including citations]
  ```

- Example filename: `persona_u_example_user.txt`.

## Security Notes

- **API Keys**: Keep your Reddit `client_secret` and Hugging Face `api_key` secure. Do not share them publicly or commit them to version control (e.g., Git).
- **Rate Limits**: Respect Reddit's API rate limits to avoid being temporarily banned.

## Dependencies

- `praw`: Python Reddit API Wrapper (`pip install praw`)
- `huggingface_hub`: Hugging Face Inference API client (`pip install huggingface_hub`)
