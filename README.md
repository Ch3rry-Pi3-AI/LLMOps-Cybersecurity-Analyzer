# 🛡️ LLMOps Cybersecurity Analyzer — Semgrep Setup & Environment Configuration

This branch focuses on two tasks:

* Setting up **Semgrep**, the static analysis engine used alongside the LLM
* Creating your local **`.env`** file containing your API keys

It follows the same structure and tone as the previous branch README, with your image references inserted exactly where you provided them.



## Step 1: Create Your Semgrep Account

Semgrep provides the static code scanning capability used by the analyzer.
Start by creating your account:

1. Visit **[https://semgrep.dev](https://semgrep.dev)**

<p align="center">
  <img src="assets/semgrep/landing_page.png" alt="Semgrep landing page" width="100%">
</p>
  
2. Click **“Try Semgrep for free”**
3. Choose **“Continue with GitHub”**
4. Authorise Semgrep when prompted

Once you're logged in, you’ll need to create an API token.



## Step 2: Generate Your Semgrep API Token

1. Click **Settings** (bottom-left corner of the Semgrep dashboard)
2. Navigate to **Tokens**

<p align="center">
  <img src="assets/semgrep/tokens.png" alt="Semgrep landing page" width="100%">
</p>

3) Click **“Create New Token”**
4) Configure the token:

   * Name: `cyber-analyzer` (or anything meaningful)
   * Scopes:

     * ☑️ **Agent (CI)**
     * ☑️ **Web API**
5) Click **Create**
6) **Important:** Copy the token immediately — it won’t be shown again

It will look something like:

```
eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9...
```

Keep this token ready — you'll add it to your `.env` file shortly.



## Step 3: Create the `.env` File

Your backend requires two environment variables:

* `OPENAI_API_KEY`
* `SEMGREP_APP_TOKEN`

To create the file:

1. In VS Code or Cursor, right-click the project root
2. Select **New File**
3. Name it exactly:

```
.env
```

4. Add:

```
OPENAI_API_KEY=your-openai-key-here
SEMGREP_APP_TOKEN=your-semgrep-token-here
```

5. Replace the placeholder text with your real keys
6. Save the file

### Security Note

Your `.env` file is already listed in `.gitignore`, so it **will not** be committed to Git.
Always keep these keys private.



## Step 4: Verify Your Keys

Your `.env` file should resemble:

```
OPENAI_API_KEY=sk-proj-abc123xyz...
SEMGREP_APP_TOKEN=eyJ0eXAiOiJKV1QiLCJhbGc...
```

Once this is done, your backend will be able to:

* authenticate with OpenAI
* authenticate with Semgrep
* run full static + LLM security analysis
