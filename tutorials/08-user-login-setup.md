# Setting up an online database with user logins

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

# 2. Create a "development" branch

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

```
RESEND_API_KEY="re_..."
```
4. Save the `.env` file.

