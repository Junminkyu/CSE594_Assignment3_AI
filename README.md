# Reddit Sarcasm Labeling Task

Participants label ten randomly selected Reddit comments as **sarcastic** or
**not sarcastic**. The comments are sourced from the Assignment 2
`sarcasm.json` dataset.

The `comments` database table stores each record's `reddit_id`, `label`,
`parent_comment`, and `subreddit`. When a participant first sees a comment,
the app calls the OpenAI Responses API with the same model, prompt, and
structured output format used in Assignment 2. The resulting assessment and
reasoning are then shown beneath that comment for the rest of the
participant's active session.

Each `submissions` row stores the participant ID, the full Reddit context
(`reddit_id`, `subreddit`, `parent_comment`, and `comment_text`), the original
dataset label (`dataset_label`), the participant's selected label, and whether
the participant was born in the United States (`born_in_us`).

## Run locally

1. Create and activate a virtual environment:

   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Configure the required environment variables:

   ```bash
   export SECRET_KEY="replace-with-a-random-secret"
   export DATABASE_URL="postgresql://USER:PASSWORD@HOST:PORT/DATABASE"
   export OPENAI_API_KEY="your-openai-api-key"
   ```

   Optionally, set `OPENAI_MODEL` to override the Assignment 2 default model
   (`gpt-5-mini`).

4. Start the development server:

   ```bash
   flask --app app run --debug
   ```

5. Open `http://127.0.0.1:5000` in a browser.

## Checking results

Open `/results` to view the labels that participants submitted.
