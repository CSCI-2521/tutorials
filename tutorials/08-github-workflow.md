# GitHub workflow tutorial

In this tutorial you will practice the basic GitHub workflow using AI coding agents in VS Code and ChatGPT. The agents will run the commands for using GitHub, and you will check every step on GitHub yourself.

Five words you will see the whole way through:

- **Branch**: a copy of your project where changes can be made safely, without touching the main version. You can make a new branch on github.com, or an agent can make one for you.
- **Worktree**: a folder on your computer that holds one branch. Different branches live in different folders, so agents can't try to edit the same file. Agents will create these for you.
- **Commit**: a saved snapshot of your changes, with a short note describing them. This can be done on your computer and then "pushed" up to github.com, or you can commit a change manually on github.com.
- **Push**: Pushing a change from your local copy of the repo on your computer up to Github.com. 
- **PR (pull request)**: a page on GitHub that collects a bunch of related commits and lets someone review them before they get merged into the main project.
- **Merge**: integrating your changes into the main version of the project.

# 1. Create a branch and a worktree

Choose one of your repos that already exists, and that you already have copied/cloned on your local computer. Make sure you have it open in ChatGPT and VS Code. If you don't already have at least one such project, please go back and complete [Tutorial 6](https://github.com/CSCI-2521/tutorials/blob/main/tutorials/06-making-a-github-repo.md).

1. Open your project in the ChatGPT app (on your computer, not on chatgpt.com).
2. Tell the agent:

```
Create a new worktree with a new branch called add-smiley.
Tell me the folder path of the new worktree.
```

The agent should confirm and should give you a path to the worktree folder on your computer like this:

<img height="200" alt="image" src="https://github.com/user-attachments/assets/af666bff-7b5e-4be6-b467-05e7a61dec33" />

# 2. Make a change with the agent

1. Tell the agent (still working in the new worktree):

```
Add a 😀 emoji to the very top of README.md.
If there is no README.md, create one with just the emoji at the top.
Then commit and push. Be quick, no tests.
```

2. Wait for it to finish.

<img width="849" height="250" alt="image" src="https://github.com/user-attachments/assets/d1bbd8b6-3a51-4ce1-be7f-895fc630d816" />

# 3. Look at the worktree folder on your computer

1. Copy the worktree folder path from Step 1. 
2. Open the terminal on your computer
3. Run this command to list the contents of the worktree folder (Your folder path will be different from mine.):
```
bash
ls /Users/danknights/example-chat-1/.worktrees/add-smiley
```
This folder should have copies of all the files in your repo. Yours will look different from mine, but it should at least contain a file called `README.md`:

<img height="100" alt="image" src="https://github.com/user-attachments/assets/61b18112-205e-4587-b04b-9ee2b43bcddb" />

4. Close the terminal window. 

# 4. Find this new branch and the commit on GitHub

1. Go to github.com and open your repository.
2. Click the branch dropdown at the top left (it says "main"). Choose the new branch, `add-smiley`.

<img height="350" alt="image" src="https://github.com/user-attachments/assets/d0090117-9772-404e-a51f-3b495df4b2f8" />

3. Scroll down if needed to look at the `README.md` file. It should have a 🙂 at the top.

Look at `README.md`. There should be a smiley face at the top.

<img height="130" alt="image" src="https://github.com/user-attachments/assets/08f1ff2c-54b0-4357-b1fe-68ba5655d408" />

3. Look near the top of the repo file list. You should see the "commit" listed, similar to this:

<img height="190" alt="image" src="https://github.com/user-attachments/assets/5f8d833b-2e4e-4e4c-9e06-ff994a196d2a" />

4. Click here to see the commit history for the repo:

<img width="1317" height="197" alt="image" src="https://github.com/user-attachments/assets/f251ccb3-a256-4a2f-80ba-e98d4280c77b" />

5. You should see a list of all commits that have been made in the repo. Click the one that added the smiley face (should be the most recent one). 

<img height="200" alt="image" src="https://github.com/user-attachments/assets/7452f10d-0d4a-47eb-b02a-15f3e527c2a7" />

6. You can see here everything that was changed in this commit (probably just the smiley face added):

<img height="650" alt="image" src="https://github.com/user-attachments/assets/27bd0f93-8772-4960-9951-6011ac699a63" />

7. Go back to the repo home page, and back to the "main" branch.

<img width="332" height="315" alt="image" src="https://github.com/user-attachments/assets/301905ab-a673-4cfd-8e2f-026096d2f757" />

The smiley face should be gone from the README.md file.

# 5. Open a draft PR

1. Tell the ChatGPT agent:

```
Open a draft pull request from this branch into main.
Give me a direct link to the PR.

Please see review comment on PR. Please fix.
Then mark the pull request as ready for review.

Add a brief comment to the PR explaining what you did.
Sign the comment "Agent 1" and include your model name.
```

2. Go back to the PR, refresh, and see the new comment.


# 6. See the draft PR on GitHub

1. Go back to the repo web site. 
2. At the top, click "Pull Requests"

<img height="50" alt="image" src="https://github.com/user-attachments/assets/b646ca1d-0521-4cdc-88e4-34bedc56dd74" />

2. Click on the pull request:

<img height="150" alt="image" src="https://github.com/user-attachments/assets/b11fbaf8-f088-4d96-be2e-8f410cd652a2" />

3. You should see a comment from the agent, the history including the recent commit, and a place to add more comments:

<img height="800" alt="image" src="https://github.com/user-attachments/assets/cb71ed9b-109f-4377-ba0c-fb3d43a3930d" />

Also notice that the PR is marked "not ready". That will change near the end. 

4. Leave the link open, you will come back to it.

# 7. Get a review and comments from a second agent

1. In VS Code, open a second agent (your reviewer).
2. Tell it:

```
Review PR #1.
Post your review as a comment on the PR.
In the review, request one change:
replace the 😀 emoji with a 🤗 emoji.

Sign your comment "Agent 2" and include your model name.
```

The agent should confirm. This cost $0.01!

<img width="600" alt="image" src="https://github.com/user-attachments/assets/8fbf98ff-2577-47ce-b4da-f2817a9dc467" />

...

<img width="600" alt="image" src="https://github.com/user-attachments/assets/90ee5d62-a612-451b-b114-34207714066c" />

3. Go back to your PR page on GitHub, refresh, and confirm there is a review comment asking for the 🤗 emoji.

<img width="600" alt="image" src="https://github.com/user-attachments/assets/784c5a21-e087-4d2b-8a60-4164f6b6b192" />

# 8. Have Agent 1 read the comment, fix it, and mark the PR ready for review

1. Switch back to your first agent in ChatGPT and tell it:

```
Please see review comment on PR. Please fix.
Then mark the pull request as ready for review.

Sign your commit "Agent 1" and include your model name.
```

2. When it is done, go back to your PR page on GitHub, refresh, and confirm there is a final comment from Agent 1.

<img width="600" alt="image" src="https://github.com/user-attachments/assets/411ca902-2c4b-45c7-bc3f-a63e6470c35f" />

3. Confirm the PR is marked "Ready for merge"

<img width="600" alt="image" src="https://github.com/user-attachments/assets/312240c0-9ce5-4eca-8d35-3c712accf7aa" />

Note: Normally, we would iterate here and do a code review from Agent 2 and more fixes from Agent 1 before marking this ready.


# 11. Merge and verify

1. On the PR page on GitHub, click the **Ready to merge** button
2. Confirm the merge.

<img width="375" alt="image" src="https://github.com/user-attachments/assets/71722e3d-01d8-40e5-be98-ea8671ea21ae" />

<img width="375" alt="image" src="https://github.com/user-attachments/assets/874250b5-a568-4406-981b-b09b3ad6141d" />

3. Go back to the home page of the repo by clicking "< > Code" top left:

<img width="200" alt="image" src="https://github.com/user-attachments/assets/a3e92d58-7d07-47c9-b9c9-9af039da9dca" />

4. Make sure the branch dropdown at the top left shows `main`.

<img width="321" height="127" alt="image" src="https://github.com/user-attachments/assets/37b86637-a62b-4554-b738-10c3a860ec0d" />

4. Scroll down to `README.md` and check that the hugging face emoji (🤗) is now there on the main branch.

<image: the merge confirmation on GitHub>

<img width="199" height="173" alt="image" src="https://github.com/user-attachments/assets/097b5421-e336-4b1f-8352-7aa0f6c93dfc" />

# 12. Clean up

1. Go back to Chat GPT (agent 1) and ask it to delete the branch an worktree; we don't need them anymore.
```
Merged. please delete the branch and worktree
```

---

🎉 Congratulations! You have gone all the way around the loop: a branch, a worktree, a commit, a PR, a review, a fix, and a merge.




