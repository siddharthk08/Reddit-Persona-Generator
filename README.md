# Reddit-Persona-Generator

# Reddit User Persona Generator

This tool uses Reddit's public data and LLaMA 3 (via Groq API) to generate a detailed user persona for any Redditor. The persona includes attributes like occupation, interests, personality, etc., and also provides citation links from Reddit posts/comments that support the AI's conclusions.

---

## Setup Instructions

Follow these steps exactly to get it running:

---

### 1. Create a Reddit App (for `client_id` and `client_secret`)

1. Go to: [https://www.reddit.com/prefs/apps](https://www.reddit.com/prefs/apps)
2. Scroll down and click **"Create another app"** or **"Create app"**.
3. Choose **"script"** as the app type.
4. Fill out the form:
   - **Name**: Anything you like (e.g., "PersonaScript")
   - **Redirect URI**: Just use `http://localhost:8080`
   - **Description**: Optional
5. Click **"Create app"**.
6. After it's created, copy the following:
   - `client_id`: the string under the app name
   - `client_secret`: the long string labeled "secret"

---

###  2. Create a Groq API Key (for LLaMA 3 access)

1. Go to: [https://console.groq.com/keys](https://console.groq.com/keys)
2. Log in and click **"Create Key"**.
3. Give it a name like "Reddit Persona App" and create it.
4. Copy the key that starts with `gsk_...` — this is your **GROQ_API_KEY**.  
(Used Groq API for LLM as it contains open source llms like LLma,it excuetes prompts without being downloaded to local drive,as to excuete the given prompting task it requires configurations and computaional resources)

---

### 3. Create a `.env` File (for environment variables)

In the root folder of your project, create a file named `.env` and paste:

GROQ_API_KEY=your_groq_api_key_here  
client_id=your_reddit_client_id_here  
secret_key=your_reddit_secret_key_here  
user_agent=Reddit Persona Script by u/your_reddit_username  


Make sure:
- There are **no quotes** around values
- The file is **not named `.env.txt`**

---

### 4. Using LLaMA 4 via Groq

This script uses the `llama-4-scout-17b` model hosted on Groq's platform. It takes the user's Reddit history, builds a structured prompt, and sends it to Groq's LLaMA 3 API using the Python.

The model then responds with a full persona and Reddit citation references for each trait. The output is streamed live and saved to a `.txt` file.

---

### 5. Set Up Your Python Environment

Install all required packages:

```bash
pip install -r requirements.txt
```

```requirements.txt should include 
praw (used to connect to Reddit’s API.It allows us to easily access a user's public submissions and comments using simple Python code.We use it here to fetch the Redditor’s posts and comments for persona analysis)
groq
python-dotenv
```

How to Run the Script
### 1.In terminal or VS Code:
python main.py
### 2.Then enter a Reddit profile URL when prompted:
Enter Reddit profile URL: https://www.reddit.com/user/xyz/ (For example)
### 3.The output will be streamed in your terminal and saved as:
C:/Users/YourUsername/Downloads/persona.txt
   
( The tester can edit the path of particular local drive in save to file section in the last line of code for eg."save_to_file(persona_text, username, folder_path="C:/Users/admin/Documents/reddit_personas") #edit only the folder path )   
(The original API keys can't be pasted in public repository as they are confidential)
