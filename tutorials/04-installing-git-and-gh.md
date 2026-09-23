# Installing `git` and `gh` tools
In this tutorial we will get the standard tools installed for managing code and talking to github.com

# Part 1: Installing Git

## 🍎 Mac Instructions

### Step 1: Open the Terminal

The Terminal is an app where you type commands to your computer directly. It looks intimidating but it's just a text window.

1. Press **⌘ (Command) + Spacebar**. A search bar called Spotlight appears.
2. Type `terminal` and press **Enter**.
3. A window opens with your username and a blinking cursor. This is where you'll type commands for this class all semester.

**Tip:** Any time you want to open the *Terminal* app, press **⌘ (Command) + Spacebar** and start typing `terminal`.

### Step 2: Install Homebrew

Homebrew is a free tool that installs other software on Macs. We'll use it to install Git.

1. In the Terminal, copy and paste this entire line, then press **Enter**:

   ```
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

2. It will ask for your **Mac login password**. Type it and press Enter. (Important: the screen will NOT show anything as you type (no dots, no stars). That's normal. Type it blind and press Enter.)
3. It will show you what it plans to do and pause. Press **Enter** to confirm.
4. **Be prepared to wait.** This downloads a few gigabytes and can take 15-40 minutes depending on Apple's servers. Don't close the window.
5. When it finishes, look at the very end of the text in the Terminal. There is a section called **"Next steps"** with a line that starts with something like:

   ```
   echo >> /Users/yourname/.zprofile
   ```

   **Copy those "Next steps" lines** (usually two lines), paste them into the Terminal, and press Enter after each one. This makes Homebrew work in new windows — skipping this is the #1 cause of "command not found" errors.

### Step 3: Install Git

1. Close the Terminal and open a **new** one (⌘+Space, type `terminal`, Enter). This is required because the new window needs to see Homebrew.
2. Type this and press Enter:

   ```
   brew install git
   ```

3. Wait a minute or two until you see your username again.

### Step 4: Check that it worked

Type this and press Enter:

```
git --version
```

You should see something like `git version 2.50.1`. Any version number = success.

---

## 🪟 Windows Instructions

### Step 1: Install Git

1. Open your web browser (Edge or Chrome) and go to: **https://git-scm.com/download/win**
2. Click **"Git for Windows/x64 Setup"** to download the installer.
3. Open the downloaded file from your browser's downloads (or the Downloads folder).
4. If Windows asks "Do you want to allow this app to make changes?" click **Yes**.
5. Click **Next** through every screen, leaving every option at its default. Just keep clicking **Next**, then **Install**, then **Finish**.

### Step 2: Open a NEW terminal

You need a fresh window for Git to be found.

1. Click the **Start menu** (Windows icon in the bottom-left corner).
2. Type `powershell` and press **Enter**.
3. A blue/dark window opens. This is your terminal. You'll use it all semester.

### Step 3: Check that it worked

Type this and press Enter:

```
git --version
```

You should see something like `git version 2.50.1.windows.1`. Any version number = success.

**If you see an error** like "git is not recognized": close PowerShell, open a new one, and try again. If it still fails, restart your computer and try once more.

---

*Both platforms done? You're ready for the next step: installing the GitHub CLI (`gh`).*

---

# Part 2: Installing the GitHub CLI (`gh`)

`gh` is a helper tool made by GitHub. It handles logging in for you, so you never have to deal with passwords or tokens when pushing code. You install it once today and it quietly does its job all semester.

## 🍎 Mac Instructions

### Step 1: Install `gh` with Homebrew

1. Open the Terminal (⌘ + Space, type `terminal`, press Enter).
2. Type this and press Enter:

   ```
   brew install gh
   ```

3. Wait a minute or two until you see your username again.

### Step 2: Check that it worked

Type this and press Enter:

```
gh --version
```

You should see something like `gh version 2.x.x`. ✅ Any version number = success.

**If you see "command not found":** close the Terminal, open a brand new one, and try again.

---

## 🪟 Windows Instructions

### Step 1: Install `gh`

1. In your browser, go to: **https://cli.github.com/**
2. Select the **Windows -- Download MSI** option from the dropdown, then the "Install button"
<img width="275" alt="image" src="https://github.com/user-attachments/assets/0b5ffb79-d346-471d-b322-343c22d39771" />

3. Open the downloaded file from your Downloads folder.
4. If Windows asks "Do you want to allow this app to make changes?" click **Yes**.
5. Click **Next** through every screen, then **Install**, then **Finish**.

*(Alternative: if you're comfortable with PowerShell, `winget install GitHub.cli` does the same thing.)*

### Step 2: Check that it worked

1. **Close PowerShell and open a NEW one** (Start menu → type `powershell` → Enter). This is required. The new window needs to see the freshly installed program.
2. Type this and press Enter:

   ```
   gh --version
   ```

You should see something like `gh version 2.x.x`. ✅ Any version number = success.

**If you see "not recognized":** close PowerShell, open a new one, try again. Still failing? Restart the computer and try once more.

---

# Part 3: Log in to GitHub (`gh auth login`)

You only do this **once**. After this, pushing code up to `github.com` never asks for a password again.

### Before you start

- Create a GitHub account. If you don't have one, go to https://github.com in your browser and create one (free). I suggest using your personal email because your university email may not be permanent.

### The login steps (identical on Mac and Windows)

1. Open your terminal (Terminal on Mac, PowerShell on Windows).
2. Type this and press Enter:

   ```
   gh auth login
   ```

3. You'll be asked a series of questions. Use the **arrow keys** to move up and down, and press **Enter** to choose. Answer like this:

   | Question | Choose |
   |---|---|
   | What account do you want to log into? | **GitHub.com** |
   | What is your preferred protocol for Git operations on this host? | **HTTPS** |
   | Authenticate Git with your GitHub credentials? | **Yes** |
   | How would you like to authenticate GitHub CLI? | **Login with a web browser** |

4. The terminal shows a **one-time code**, like `XXXX-XXXX`. **Write it down or leave the window visible**, then press **Enter**. Your web browser opens.
5. In the browser, sign in to GitHub if asked, then paste the one-time code into the box and click **Continue**.
6. Click the green **Authorize github** button.
7. Go back to your terminal. You should see: `Logged in as your-username`.

### Check that everything works together

Type these one at a time, pressing Enter after each:

```
git config --global user.name "Your Name"
```

```
git config --global user.email "the-email-you-used-for-github@example.com"
```

⚠️ Use the **same email you signed up for GitHub with** — this is how your commits get linked to your account on the website. Keep the quotation marks, and replace "Your Name" with your actual name.

### Final test

```
gh auth status
```

You should see a checkmark next to both `github.com` and `git`. ✅

---

# 🎉 Tutorial Complete

You now have set up on your computer:

- ✅ **Git** — the version control engine
- ✅ **gh** — your automatic login to GitHub
- ✅ **A working login** — no passwords needed for the rest of the semester

Next up: sign up for web hosting services in [tutorial 05](05-web-hosting-setup.md).

