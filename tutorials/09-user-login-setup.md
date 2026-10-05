# Setting up an online database with user logins

# Warning - no private user data

**Please do not use any private user data in your app for this class.** I am providing instructions below for you to enable user authentication or login on your app using a database for educational purposes. But I strongly recommend that you take more CS classes and gain confidence in reading code before you manage real user data in your app. 

# 0. Create .env and .gitignore files
Before setting up the database, make sure you already have a github repo created, and you have cloned it to your computer as in [Tutorial 6](https://github.com/CSCI-2521/tutorials/blob/main/tutorials/06-making-a-github-repo.md). This could be your project repo (Part 1) or another repo you have created (Part 2). 

1. Open the folder for your local copy of the repo in VS Code.
2. In VS Code, click File > New Text File (or New File) to create a new file, and save it as `.env`. If you already have a `.env` file, open it.
3. Add these entries to the file: 

```
DATABASE_URL=
RESEND_API_KEY=
RESEND_FROM_EMAIL="Your app name <onboarding@resend.dev>"
FLASK_SECRET_KEY=
APP_BASE_URL=http://127.0.0.1:5000
```

4. Save the file.
   
Note: you will fill in the missing values later. You can change "Your app name" to your app name, but do not change the email, `onboarding@resend.dev`.

5. Still in VS Code, click File > New Text File (or New File) to create another new file, and save it as `.gitignore`. If you already have a `.gitignore` file, open it.
6. Add this to the `.gitignore` file:

```
.env
```
This will ensure that git does not upload your secret `.env` file to github.com.

7. Save the file. 


# 1. Create an online database (already done in tutorial 5)
Neon provides free permanent databases. You should have done this in [tutorial 05 Part 1](https://github.com/CSCI-2521/tutorials/blob/main/tutorials/05-web-hosting-setup.md); if not, please go there and do Part 1. 

# 2. Create a "development" branch in your database

When you make a real app, you don't want to change the real database (the "production") database while you are developing and testing new features. So instead we make a separate "branch" of the database that is specifically for development, as follows. 

1. Go to the dashboard for your database on neon.com. You may need to click the name of the database. Then click "Branches", and "New Branch":
<img height="250" alt="image" src="https://github.com/user-attachments/assets/0d528385-e503-4241-ae6a-f20d3e594db4" />

2. Fill in the new branch details like this, then click "Create". :

 - Name it development.
 - Disable Auto-delete so it remains available.
 - Parent branch: production.
 - Choose Branch schema only.

<img height="450" alt="image" src="https://github.com/user-attachments/assets/3a7b5702-880c-4ecf-be1a-428ebb85b41f" />

3. Click "Copy snippet" to copy the connection string:

<img height="370" alt="image" src="https://github.com/user-attachments/assets/50be20d3-f7ee-4682-b26b-36b549fd7c36" />

4. Paste the connection string into your `.env` file as the `DATABASE_URL` value:

```
DATABASE_URL="postgresql://neondb_owner:....."
```

5. Save the `.env` file.

# 3. Get a free email sending service (Resend.com)

In order to get logins working, we need a way for our code to send emails. An easy free service is Resend. We will set up an account there and get an API key. 

1. Sign up at [resend.com](https://resend.com).
2. Get an API key. Resend may offer this right after you register. If not, then look for "API Keys" link, might be on the left:
<img height="350" alt="image" src="https://github.com/user-attachments/assets/0ef1c7cb-18e9-4821-84ba-452c78358a9c" />
3. Copy and paste the API key value into your `.env` file as the `RESEND_API_KEY` value:

Note: the free version of "resend" only allows you to send emails to your own email address. So you can't have testers log in. 

```
RESEND_API_KEY="re_..."
```

4. Save the `.env` file.

# 4. Generate a secret key for your web server

Your web server needs a secret code that it can use to "sign" login attempts.

1. Go to the terminal app on your computer
2. Open a new terminal window
3. Run this python command:

```
python -c "import secrets; print(secrets.token_urlsafe(32))"
```

4. Copy the output and save it in your .env file:

```
FLASK_SECRET_KEY="Paste the secret code here"
```

5. Save the .env file.

Your .env file should now have every environment variable defined:

```
DATABASE_URL="postgresql://neondb_owner:..."
RESEND_API_KEY="re_..."
RESEND_FROM_EMAIL="Your app name <onboarding@resend.dev>"
FLASK_SECRET_KEY="ABCDEf...."
APP_BASE_URL=http://127.0.0.1:5000
```

# 5. Put the secrets in Render

1. Go to your web services page and click "Environment"

<img height="400" alt="image" src="https://github.com/user-attachments/assets/a285ab2b-8eda-492c-9534-38a87603c482" />

2. Click "Edit", then the eye symbol to edit the .env file:

<img height="350" alt="image" src="https://github.com/user-attachments/assets/2838eab7-ed91-4965-8f56-a25bb0f8ae65" />

3. Paste in the values from your local .env file. Mine are redacted here.
   
<img height="450" alt="image" src="https://github.com/user-attachments/assets/bc02f15d-6594-4550-8c23-4b812b45eda3" />

5. Change the database URL to your production database connection string, as follows:
   1. Go to neon.com, select your production branch, and click "Connect":
  <img width="219" height="134" alt="image" src="https://github.com/user-attachments/assets/7e8e214a-00b1-4d9d-b7e0-ee542c2566f1" />

   1. Copy the connection string:

<img height="400" alt="image" src="https://github.com/user-attachments/assets/508a43f1-2608-483b-bbdc-7ea4e8f85f32" />
  
   1. Paste this into your .env file as the `DATABASE_URL` back on Render, and click "Done". 
   
<img height="450" alt="image" src="https://github.com/user-attachments/assets/04a66b4a-e21a-4ed0-93d0-66419b5edbc3" />


# 6. Ask your agent to set up magic-link logins using Neon and Render

This is an example prompt. Please read it before using it, and modify if needed. This tells the model to use a number of best practices to avoid common ways for people to abuse your Web server. This does not cover all security bases, though, especially once you start adding more features to your app.

Above all, remember, no private user data should be uploaded to your app for your class project, and until you are confident in your security practices (more CS classes). Also consider asking powerful agents to do a security review of your app, although it will still requires CS training to interpret most of the results.

```
Please build the login system for my web app. Don't add any other 
features yet. Let's use Flask in Python for the server.

Use Neon as the authorization and user manager and database,
and use Render as the email sender.

Write a short plan first so I can check it before you write
the code. Explain every part in plain language for someone
who has never written code.

When you are done, tell me:

1. How to set up the development database from my local computer. 
2. How to run the app locally for testing
3. what to put for the startup command on Render.
Make sure you include a command to 
set up the production database on launch, so that I won't have
to put my production database secret on my local computer. For example:

python setup_db.py && gunicorn app:app

Here are the environment variables you can expect
on Render and in my local .env file:

DATABASE_URL="postgresql://neondb_owner:npg_..."
RESEND_API_KEY="re_..."
RESEND_FROM_EMAIL="Puzzle Demo onboarding@resend.dev"
FLASK_SECRET_KEY="W..."
APP_BASE_URL="http://127.0.0.1:5000"

The DATABASE_URL in my local .env file will be for the
development branch of the database. The DATABASE_URL on 
Render's .env file will be the production branch. 

On my local computer, we will use APP_BASE_URL for generating
the magic sign-in links. On Render, I will leave out APP_BASE_URL.
Render will have a variable RENDER_EXTERNAL_URL that you should 
use instead. 

WHAT TO BUILD
Users sign in by entering their email, receiving a one-time sign-in link, and clicking
it. 

TOOLS AND SETTINGS
- Neon PostgreSQL; read its address from DATABASE_URL.
- Send email with Resend; read RESEND_API_KEY and RESEND_FROM_EMAIL from
  the environment.
- Read FLASK_SECRET_KEY from the environment (a long random string I generated)
- The app's own URL comes from APP_BASE_URL on my computer and
  RENDER_EXTERNAL_URL on Render. Build links from these.
- Never put secrets in the code.

DATABASE
Make two tables, created by a setup command that is safe to run more than once.
- users: id, lowercase email, created_at.
- login_tokens: id, user_id, a hash of the sign-in code (never the code
  itself), expiry time, used time, created_at.

HOW SIGN-IN WORKS
1. The home page shows an email form, or the logged-in state.
2. Submitting the form checks and lowercases the email (use a standard
   email-validation library), creates the user if new, cancels their old
   unused links, makes a fresh random code with a standard cryptographic
   generator (32+ bytes), stores only its hash, and emails a link.
3. Limit this to about 3 requests per hour. The counter lives in server
   memory, so it's approximate which is fine for this project.
4. The emailed link opens a "confirm sign-in" page with a button; it must
   NOT sign the person in by itself. Reason: some email programs open
   links automatically to scan them, which would use up a one-time link
   before the human clicks.
5. Clicking the button checks the code, checks expiry, and marks it used
   in one single database step — the same link can never work twice, even
   with two requests at the same instant. Links expire after 15 minutes.
6. Success starts a brand-new session with secure cookies (Secure,
   HttpOnly, SameSite=Lax) and remembers the user's id.
7. A logout button clears the session.

SAFETY RULES
- Invalid, expired, or already-used links show a generic message. Never
  say whether an email has an account.
- Every form that does something (request link, confirm sign-in, logout)
  must reject forged submissions (a form-protection library like
  Flask-WTF is fine). This means our forms have a secret handshake so that
  other pages can't submit fake forms.
- Server logs must never contain full email addresses or the sign-in links
  themselves.
- Email or database failures are logged server-side and shown to the
  user as "something went wrong, please try again."
  
DEPLOYMENT
- Runs on Render, so please document the exact start command.
- Tell me how to set up the database before deploying this.

TESTS
- Unit tests: email handling, code hashing, expiry, one-time-use,
  config fallback.
- Page tests with Flask's test client: request a link, sign in with a
  valid link, reject invalid/expired/reused links, log out.
- Wrap email sending behind a small "mailer" boundary so tests never send
  real email.
```

# 7. Follow your agent's instructions to test locally on your computer
Remember that Resend will only let you log in with your own email.

# 8. Ask your agent to commit and push
Agent commits and pushes to github.com; Render should re-deploy automatically.

# 9. Debug if needed
If anything doesn't work, don't panic. You can review these instructions to make sure you didn't miss anything. Then ask an agent for help and tell them what error message you got. 
