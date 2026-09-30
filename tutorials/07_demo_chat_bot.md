# Making and deploying a chat bot

# Part 1. Getting it running locally
In this tutorial, we will make a simple LLM chat bot and deploy it up to the internet on Render.com.

Disclaimer: we will not follow our normal coding practices for this because it is just a demo that we are planning to throw away afterward. The point of this exercise is to practice pushing and deploying the code, not to practice agentic coding. This is a very simple app that is easy for the LLM to write, and it doesn't have any features, so it will work fine without the reviewing loop.

## 1. Create a new repo

See Part 2 in tutorial [tutorial 6](06-making-a-github-repo.md).

## 2. Copy it to your computer and open it in VS Code and ChatGPT 

See Part 1 steps 4, 5, 6 in [tutorial 6](06-making-a-github-repo.md).

## 3. Build the app
You will prompt ChatGPT to build the app. You can say it any way you want, but this will work:

If you're using TensorX for LLM inference:
```
write a chat app that talks to an LLM. write this as a web app in python that I can deploy online later.

The API address (url) is https://api.tensorx.ai/v1
Please use this model: deepseek/deepseek-v4-flash-0731

I am going to supply the API key in a .env file. Please make an .env file for me to add the API key called TENSORX_API_KEY.
```

If you're using OpenRouter for LLM inference:
```
write a chat app that talks to an LLM. write this as a web app that I can deploy later in python.

The API address (url) is https://openrouter.ai/api/v1/
Please use this model: deepseek/deepseek-v4-flash-0731

I am going to supply the API key in a .env file. Please make an .env file for me to add the API key called OPENROUTER_API_KEY.
```

Note: if you already built your app and did not specify Python, please ask ChatGPT to rebuild it:

```
If this is not already built in Python, please rewrite it in Python.

If this is not a web app, please rewrite it as a web app so I can deploy it online.
```

Note: if you already built your app and it's not working, you might have to tell it which model to use:

```
Please use this model: deepseek/deepseek-v4-flash-0731
```

We are using Python to make it the same for everyone to deploy on Render.com.

## 4. Approve the design if needed

Approve the design if ChatGPT asks you to (you may have to expand the "Worked for..." field to see the plan. 

```
approved
```

## 5. Add your API key
Create a new API key (or reuse your old one if you have it somewhere) on [TensorX.com](https://app.tensorx.ai/dashboard/keys) or [OpenRouter.com](https://openrouter.ai/workspaces/default/keys).

Go to VS code and look for the `.env` file in the file Explorer. Click on that file, add your API key, and save (File -> Save). 

<img height="465" alt="image" src="https://github.com/user-attachments/assets/60e00064-0f16-4531-8530-7457b57412bf" />

Your `.env` file should have a line that looks like this:
```
TENSORX_API_KEY=sk...
```

or this:

```
OPENROUTER_API_KEY=sk...
```

Be sure to save the file (will look slightly different on Windows):

<img height="420" alt="image" src="https://github.com/user-attachments/assets/da5c92da-8475-4931-b7fe-5598a766f0b1" />


## 6. Try out the app

Ask ChatGPT to start the app:
```
Please start the app so I can try it and give me a link.
```

## 7. Debug if needed

If your app doesn't work, tell ChatGPT. Be sure to copy and paste any errors that you see, or give it a screenshot.

At the end of this step, your app should be working on your local computer.

```
Not working. Got this error: ... (paste error or screen capture, or describe what happened)
```

---
# Part 2: Deploy online

## 1. Commit and push to Github.com

Ask ChatGPT to commit the code and push it up to Github:

```
Please commit and push.
```

## 2. Connect a Render Web Server

### 1. Go to Render.com.

### 2. Create a new web service
When you are logged in, you may see the Dashboard offering to set up a service. Select "Web service"

<img width="950" height="361" alt="image" src="https://github.com/user-attachments/assets/2a950f40-b8e5-45c0-8044-1fd8f651d289" />

If you don't see this, click "Dashboard" top right: 

<img height="90" alt="image" src="https://github.com/user-attachments/assets/8a66c2b0-7866-46b7-bd79-6f3597ccd92f" />

If you don't see that, find another way to get to your Dashboard until you see the "+ New" button top right. Then click this and select "New web service": 

<img height="350" alt="image" src="https://github.com/user-attachments/assets/ed701b94-3331-4ebd-a46e-d78527693b83" />


### 3. Authorize Render on Github

If you haven't done this already, click "GitHub" to connect your github account to Render, then click "Authorize" in the next window.

The next window will ask you where to "install" render (on github.com). Click your personal account name.
<img height="300" alt="image" src="https://github.com/user-attachments/assets/6e107204-5557-4df7-a55e-cf56971edaf3" />

### 4. Select your new repo
On the next page, find your new repo in the search list: 
<img width="413" height="124" alt="image" src="https://github.com/user-attachments/assets/0142b906-3010-43ee-acf7-f62ac18bf4b5" />

### 5. Set the Language to Python

<img height="800" alt="image" src="https://github.com/user-attachments/assets/079321c6-1de1-4cfb-9d27-3be8745725d8" />

### 6. Set the Root directory, Build command, and Start command

Ask ChatGPT what to use for these fields:

```
I'm putting this on Render. what should I enter for root directory, build command, and start command?
```

Then enter the values. Yours may look different from mine:

<img height="300" alt="image" src="https://github.com/user-attachments/assets/85223d08-04fb-4360-8d90-850dae57ec35" />

Be sure to choose $0

<img height="300" alt="image" src="https://github.com/user-attachments/assets/a279708a-98f0-4294-9fb2-25e6cc30e8a3" />

### 7. Add a secret file

<img height="200" alt="image" src="https://github.com/user-attachments/assets/d2d5afda-061a-461b-bc50-772359998506" />

### 8. Call it .env, enter your API key
<img height="380" alt="image" src="https://github.com/user-attachments/assets/41be2e5a-db74-4203-9f37-8b2eb10ea74f" />

### 9. Deploy

<img height="130" alt="image" src="https://github.com/user-attachments/assets/4362e8b2-d56b-4bb8-bbd9-4307b4ee64c4" />

## 3. Test the deployed app

<img height="200" alt="image" src="https://github.com/user-attachments/assets/e0cb2fe6-3ed8-4a06-b723-f5ca72032a6b" />

## 4. Debug if not working

If anything is broken, describe it to ChatGPT and push the fixes to GitHub and check Render.

🎉 Working? Congratulations! You have deployed a web app that uses an API service.

---

# Part 3: Add a feature

Try adding a feature to your app. Make one up! Something you would actually one. Do it locally, then push to GitHub and try it on Render.



