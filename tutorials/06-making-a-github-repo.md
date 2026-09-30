# Making a Github repo
This tutorial covers how to copy the repo for the course project and get it set up in VS code and ChatGPT, and then how to make a brand new repo for other testing or projects.

# Part 1. Getting your own copy of the project repo
## 1. Copy the project template
Go to https://github.com/CSCI-2521/project-template.

Click "Use this template":
<img width="373" height="198" alt="image" src="https://github.com/user-attachments/assets/fc191d61-310f-463b-b1b3-fc3f4717e6c3" />

On the next page, name it something convenient like "2521 Class Project". 

Then be sure to make the repo "private", for now:

<img height="280" alt="image" src="https://github.com/user-attachments/assets/a79e7ab1-2e51-4db9-a52f-0a252df8fc98" />

This will ensure that if you do accidentally leak an API key, it won't get shared with the whole internet. You can always make it public later.

You now have your own copy. 

## 2. Add the instructors

On your repo on github.com, click Settings:

<img width="239" height="124" alt="image" src="https://github.com/user-attachments/assets/cf57e948-4d89-4e67-bb16-ec96fc3bc0f9" />

Then Collaborators on the left:

<img height="170" alt="image" src="https://github.com/user-attachments/assets/683b1ded-6192-423a-83bb-bef32761aebe" />

Click "Add people"

<img width="604" height="272" alt="image" src="https://github.com/user-attachments/assets/9f7cf861-821b-42dd-8a1e-cb3653ae1451" />

Then add me, `danknights`.

## 3. Make your repo private if it's public

In your repo, go to Settings

<img width="167" height="90" alt="image" src="https://github.com/user-attachments/assets/966469ac-d77e-4e9a-9dca-84b183f0aa29" />

Scroll down to the "Danger Zone" and change from Public to Private:
<img width="1443" height="210" alt="image" src="https://github.com/user-attachments/assets/514e0037-4bdd-4aae-a0a9-8bc57eafa86d" />



## 4. Get a clone of the repo on your computer

On your repo on github.com, click Code and copy the path to the repo:

<img height="405" alt="image" src="https://github.com/user-attachments/assets/0096315e-18c7-4bb0-be5d-d50b46ce1aa5" />

Then go to the terminal on your computer, go to your home directory, and enter this to put the folder in your home directory (or choose a different directory if you want). 

```
cd ~ 
git clone (paste the URL you copied)
```

## 5. Open it in VS Code

File > New Window (if you already have a project open)
File > Open Folder > Find the folder you just cloned. 

Then look for a warning at the top that the folder is untrusted, and click "manage" and then click the button to "Trust" the folder:

<img height="80" alt="image" src="https://github.com/user-attachments/assets/caccf70d-05d1-4bab-9131-4fe463cc3c04" />

<img height="320" alt="image" src="https://github.com/user-attachments/assets/608d237f-3396-4ba8-a609-f80275b7b2d2" />


## 6. Open it in ChatGPT

Click "+" next to Projects

<img width="334" height="73" alt="image" src="https://github.com/user-attachments/assets/b1139915-e5af-43d0-8bb7-04d0d5ae6f3a" />

Then name the project something convenient. Then add the folder that you created that contains the code.

<img width="639" height="399" alt="image" src="https://github.com/user-attachments/assets/7d6e4230-4dd1-4f8f-bb1e-5403061b5c26" />

---

# Part 2. Making a brand new empty repo
If you are working on something that is not the class project, like you want to start something new or run a class demo, follow these instructions.

1. Go to GitHub. Make sure you are logged in. Then click "+" top right, and "New repository"

<img height="380" alt="image" src="https://github.com/user-attachments/assets/7e991a2e-5992-4632-82d2-a419382bd8e3" />

2. Name it something simple. Add a readme file, and mark the repo private:

<img height="500" alt="image" src="https://github.com/user-attachments/assets/df3bdfcb-4ba6-4868-a17a-ddf1a5803509" />

3. Follow steps 4, 5, 6 above to get a copy of it on your computer and open it in VS Code and ChatGPT. 
