# Setting up an online database with user logins

# Warning - no private user data

**Please do not use any private user data in your app for this class.** I am providing instructions below for you to enable user authentication or login on your app using a database for educational purposes. But I strongly recommend that you take more CS classes and gain confidence in reading code before you manage real user data in your app. 

# 0. Create .env and .gitignore files
Before setting up the database, make sure you already have a github repo created, and you have cloned it to your computer as in [Tutorial 6](https://github.com/CSCI-2521/tutorials/blob/main/tutorials/06-making-a-github-repo.md). This could be your project repo (Part 1) or another repo you have created (Part 2). 

1. Open the folder for your local copy of the repo in VS Code.
2. In VS Code, click File > New Text File (or New File) to create a new file, and save it as `.env`. If you already have a `.env` file, open it.
3. Add these entries to the file: 

```
DATABASE_URL=""
FLASK_SECRET_KEY=""
APP_BASE_URL="http://127.0.0.1:5000"
NEON_AUTH_BASE_URL=""
```

4. Save the file.
   
Note: you will fill in the missing values later.

5. Still in VS Code, click File > New Text File (or New File) to create another new file, and save it as `.gitignore`. If you already have a `.gitignore` file, open it.
6. Add this to the `.gitignore` file:

```
.env
```
This will ensure that git does not upload your secret `.env` file to github.com.

7. Save the file. 


# 1. Create an online database (already done in tutorial 5)
Neon provides free permanent databases. You should have done this in [tutorial 05 Part 1](https://github.com/CSCI-2521/tutorials/blob/main/tutorials/05-web-hosting-setup.md); if not, please go there and do Part 1. 

# 2. Save the connection URL in your .env
1. In Neon, go to your database, and click "Connect":
<img width="140" alt="image" src="https://github.com/user-attachments/assets/f700090a-d53a-43e1-94a5-19c1e4beae07" />

2. Copy the Auth URL:
<img width="400" alt="image" src="https://github.com/user-attachments/assets/e72f2457-8495-4a06-ac35-a9fd4e0b527a" />

3. Go back to your .env file in VS Code. Paste this into your .env file. Save the file.

<img width="1577" height="455" alt="image" src="https://github.com/user-attachments/assets/70e4edb9-27ad-43ba-bda6-f611179a5edd" />

# 3. Set up user logins on Neon
1. In Neon, go to your database, and click "Better Auth":

<img width="140" alt="image" src="https://github.com/user-attachments/assets/5cb43cc0-a357-44fd-b25a-9ea483982d7f" />

2. In the next window, click the confirmation button to set up "Enable Neon Auth".

<img width="600" alt="image" src="https://github.com/user-attachments/assets/82e5f449-d968-401e-9bb1-97a39dd58ce7" />

3. Next page, click "Configure Auth"

<img width="350" alt="image" src="https://github.com/user-attachments/assets/5633845a-9eff-475f-9ec5-0ce89217107e" />

4. Copy the "Auth URL" from Neon:

<img width="600" alt="image" src="https://github.com/user-attachments/assets/25767a11-b255-4cff-bbb9-c32394e00e0c" />

5. Paste it in your .env file as "NEON_AUTH_BASE_URL" and click File > Save.

<img width="600" alt="image" src="https://github.com/user-attachments/assets/4d83a157-c66f-4a07-9653-54c9c66606fa" />

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
FLASK_SECRET_KEY="ABCDEf...."
APP_BASE_URL=http://127.0.0.1:5000
NEON_AUTH_BASE_URL="https://..."
```

# 5. Put the secrets in Render

1. Go to your web services page and click "Environment"

<img height="400" alt="image" src="https://github.com/user-attachments/assets/a285ab2b-8eda-492c-9534-38a87603c482" />

2. Click "Edit", then the eye symbol to edit the .env file:

<img height="350" alt="image" src="https://github.com/user-attachments/assets/2838eab7-ed91-4965-8f56-a25bb0f8ae65" />

3. Paste in the values from your local .env file. Mine are redacted here. Click "Done".
   
<img width="600" alt="image" src="https://github.com/user-attachments/assets/858423e9-7e29-4af4-8f66-9e54b0d2934e" />

# 6. Finish setting up "Better Auth" in Neon
1. Go to [render.com](https://render.com) and copy your app's URL:

<img width="600" alt="image" src="https://github.com/user-attachments/assets/f78941dd-baff-4e55-ab76-f087c77bbc73" />

7. Go back to Neon Better Auth configuration (from Section #3 above) and paste the app URL into Domains > Add new domain:

<img width="600" alt="image" src="https://github.com/user-attachments/assets/841311ee-8bb3-47e4-bee1-14fa12999151" />

This tells Neon where to send users after they log in.

8. In Neon Better Auth configuration, make sure "Localhost" is turned on (allows you to run on your computer):
<img width="600" alt="image" src="https://github.com/user-attachments/assets/6c75a8f9-948a-4780-aaa3-138f2e453955" />

9. In Neon Better Auth configuration, under OAuth providers, remove "Google":

You can set it up later if needed. It's a whole extra set of steps.

<img width="600" alt="image" src="https://github.com/user-attachments/assets/a3014798-309e-4dde-928a-a0fb730ce16e" />

10. Turn off Organizations, turn on magic links with new users:
<img width="600" alt="image" src="https://github.com/user-attachments/assets/6ac6b3f1-3610-4962-b1a1-0bf6330917d8" />

# 7. Tell your agent to implement Neon-managed auth:

1. Go back to ChatGPT and start a new thread in your project

2. Tell the agent to implement Neon-managed user logins:

```
let's implement user logins, using Neon's Better Auth tool.
Read the docs here: https://neon.com/docs/auth/overview

I already have these variables in my local .env file and my .env file on Render:

DATABASE_URL="postgresql://neondb_owner:..."
FLASK_SECRET_KEY="ABCDEf...."
APP_BASE_URL=http://127.0.0.1:5000
NEON_AUTH_BASE_URL="https://..."

And I have given Neon Better Auth my app URL.

For now, don't implement any features; just allow a user to log in
with a button, and show when they are logged in. Then add a button 
for them to log out if they are logged in. You will also need a place
for them to enter the secret OTP code they are emailed when logging in.
```

# 8. Test it out locally.
1. Tell Agent 1 (e.g. ChatGPT) to start the web app on your computer and give you a link:

```
Please start the web app locally and give me a link.
```

2. Open the link, try signing in.

If it doesn't work, tell Agent 1 and tell it to check the server logs. If it does work, try it on Render.com.

# 9. Test it on Render
1. Tell Agent 1 to commit the changes and push to GitHub. 

```
Please commit these changes and push to GitHub.
```

2. Go to your Render app and wait for it to re-deploy (takes a few minutes)

3. Test logging in and logging out on Render.

If it doesn't work, go back through this tutorial and double check each step; also tell Agent 1 what happened and ask to debug and fix.

If it does work, then congratulations! You can now have users. 🎉

# 10. See your users on Neon

1. Go to Neon. Click "Better Auth" on the left. You should see the new user you created. 

<img width="600" alt="image" src="https://github.com/user-attachments/assets/3bf02ca8-0795-4c25-b8be-49a0f992faf4" />


