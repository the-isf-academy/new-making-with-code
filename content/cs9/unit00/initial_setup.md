---
weight: 1
---



# Initial setup

**Welcome! These instructions will help you get your computer set up for the class.**
If you get stuck or are unsure what to do, send a screenshot of your error to. Everyone's system is
different, so the initial setup sometimes needs some TLC.
*You should only ever have to run these instructions once.*

---

## Github

Github is a hosting service for code. It allows users to collaborate on projects and track versions of their code over time. We will be using Github to distribute code to students and for students to submit their work.

{{< code-action >}}
**Sign up for a Github account by going to [this](https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home) link.**

{{< figure src="https://github.githubassets.com/images/modules/logos_page/Octocat.png" width="25%" alt-text="Python Turtle Graphics" >}}
- Be sure to use your ISF student email.
- You will be asked to create a Github username. Do NOT use your student ID number and make sure it is school appropriate.  

{{< youtube "GmiNDSIuxZQ" >}}



---

## Initial Install
To get your computer ready, we need to configure the workspace you will use for the class. **Select the tab for your operating system and follow the instructions.** Please letknow if you run into any issues.


tab

### Installing Python
(0) **Start by installing the latest version of Python.** [Open this link](https://www.python.org/downloads/), click "Download Python," and follow the installation instructions.


(1) **Once the installation finishes, you will see a Finder window showing what was installed**.
(If you closed the window, open Finder, click on "Applications," and then "Python 3.10" (or whatever version of Python you just installed).


(2) **Check Python installed successfully by typing `python --version` into Powershell.** You should see a version number above `3.10`.

(3) **Double-click on "Install Certificates.command".** This will will open a Terminal window and run a bunch of commands. Once you see `[Process completed]`, you may close the window.

(4) **Double-click on "Update Shell Profile.command".** Each of these will open a Terminal window and run a bunch of commands. Once you see `[Process completed]`, you may close the window.


ASIDE
**If you see a red "Permission denied" error message when running "Install Certificates.command"**:
- open a Terminal window and run **`sudo "/Applications/Python 3.10/Install Certificates.command"`**
- You will be asked for an administrator password; you won't see any letters appearing as you enter the password. This is a security feature.


{{< youtube "OiCiOgeyaWA" >}}

### Installing Homebrew and Github CLI

{{< code-action "Run the below command to install homebrew." >}} This will install homebrew onto your computer. This may take up to an hour to complete. Don't worry, you can still use your computer and have it running in the background. If you already have homebrew, then this step will be quick.
```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
{{< code-action "Run the below command to install the Github CLI." >}}
```shell
brew install gh
```
{{< code-action "Run the below command to authorize." >}} This will take you through a few prompts to log in to your github account.
```shell
gh auth login
```

**You will be asked the following questions to finish the authorization process. You should accept all the default highlighted options, which are these:**

0. "What account do you want to log into?" - GitHub.com
0. "What is your preferred protocol for Git operations?" - HTTPS
0. "Authenticate Git with your GitHub credentials?" - Yes
0. "How would you like to authenticate GitHub CLI?" - Log in with a web browser

> **If you are asked for your computer password, you won't see any letters appear as you type.** This is normal--it's to keep the person standing behind you from seeing your password.

{{< code-action "When prompted, copy your code and press enter." >}} Then you can follow the prompts in your browser.


### Install Linux

### Installing Python

(0) **Start by installing the latest version of Python.** [Open this link](https://www.python.org/downloads/), click "Download Python," and follow the installation instructions.
  - Make sure you select `Add Python 3.10 to PATH'

(1) **Open Windows Powershell**. We will be using this application every class. We suggest you pin it to your toolbar.
{{< figure src="https://upload.wikimedia.org/wikipedia/commons/a/af/PowerShell_Core_6.0_icon.png" width="25%" alt-text="Python Turtle Graphics" >}}

(2) **Check Python installed successfully by typing `python --version` into Powershell.**
> You should see a version number above `3.10`

{{< youtube "uhRWvk1Cafc" >}}


### Installing Github for CLI

(0) **Go to [cli.github.com](https://cli.github.com/
) and install Github CLI**

(1) **Open Windows Powershell**

(2) **Type this command: `gh auth login`**

(3) **It will ask you a series of questions. Follow the *blue* answers below.**

{{< figure src="images/courses/cs9/unit00/-000_initialsetup1.png" width="100%" alt-text="mwc setup" >}}
> Make sure you copy your "one-time code". You will need to active your computer in the browser.

{{< figure src="images/courses/cs9/unit00/-000_initialsetup2.png" width="50%" alt-text="mwc setup" >}}

(4) **Once complete, you will see the following in your Powershell**

{{< figure src="images/courses/cs9/unit00/-000_initialsetup3.png" width="100%" alt-text="mwc setup" >}}


aside
Whenever this website says to use Terminal, you should use Windows Powershell. There will be other small differences for Windows users that we'll explain along the way.



## Install MWC

`mwc` is a special program we wrote for this class which will help you set up your assignments.

{{< code-action "Open Terminal and run the following command." >}}
```shell
pip3 install making-with-code-cli
```



{{< code-action "Copy and paste each command, one at a time, into the Terminal." >}}
- `sudo pip3 install making-with-code-cli` or
- `pip3 install --user making-with-code-cli`

Still no luck? Talk to.


{{< code-action "Check mwc installed successfully by checking the version number." >}} You should see a version number above 0.0.5, such as `MWC 0.0.53`.
```shell
mwc version
```

---

## Configure MWC

{{< code-action "Run the below command to begin the full setup." >}} This will install a few packages onto your computer. This may take up to 30 minutes to complete. Don't worry, you can still use your computer and have it running in the background.
```shell
mwc setup
```
You will be asked some questions to finish the setup process. **We suggest using the default values in the square brackets, `[]`. You can select the default value with `return`.**
> Although the screenshots below are of Mac using Terminal, it is the same process for Windows using Powershell

{{< figure src="images/courses/cs9/unit00/-000_initial_setup0.png" width="100%" alt-text="mwc setup" >}}

**You will be asked the following questions to finish the setup process:**

0. "What is your MWC username?" - Use your Github username.
0. "Where do you want to save your MWC work?" - we suggest using the default.
0. "What's the URL of your Making With Code website?" - use the default value.
0. "Which code editor do you want to use?" - use the default value.
0. "What is your GitHub username?" - use whatever username you created in the Github account creation.
0. "What is the name of the course's GitHub organization?" - this is `the-isf-academy`.
0. "What is the email address associated with your GitHub account?" - this should be your ISF student email.
0. "What name do you want to use in your git commits? " - this is your Github username.

{{< figure src="images/courses/cs9/unit00/-000_initialsetup4.png" width="100%" alt-text="mwc setup" >}}


> **When you are asked for your computer password, you won't see any letters appear as you type.** This is normal--it's to keep the person standing behind you from seeing your password.

## Testing your Installation

**Perform the following checks to be sure your installation is working properly**

{{< code-action "Run the following command in your terminal" >}}

```shell
mwc update
```
The output should be something like this:

```shell
Checking cs10/unit0.0_review/lab0_terminal_adventure_sequel for updates.
Already up to date.
```

If you are seeing just these two lines, congratulations! You're all set up and ready to go.

If you are getting more than these two lines after running `mwc update` multiple times, please inform your teacher!

