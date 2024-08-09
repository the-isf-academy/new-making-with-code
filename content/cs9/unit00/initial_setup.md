---
title: "Initial Setup"
weight: 1
---

# Initial setup

**Welcome to CS! These instructions will help you get your computer set up for the class.**
If you get stuck or are unsure what to do, send a screenshot of your error to Ms. Brown or Ms. Genzlinger.


---
## Visual Studio Code
*This is the editor that you will use to write your code.*

(0) **Download and Install.** [Open this link](https://code.visualstudio.com/), click "Download Mac Universal," or use the dropdown to select your operating system. Follow the installation instructions.

(1) **Drag to Applications Folder.** Open up the `Finder` application on your Mac. On the left hand side, click on `Downloads`.  Drag it to the folder named `Applications`.

{{< figure src="images/courses/cs9/unit00/-000_initialsetup12.gif" width="25%" alt-text="mwc setup" >}}

(2) **Install Shell Commands.** Open up your freshly installed `Visual Studio Code` application. From the top menu, select `View > Command Pallete`. 

{{< figure src="images/courses/cs9/unit00/-000_initialsetup7.png" width="75%" alt-text="mwc setup" >}}

In the prompt, type `Shell Commands` and click on the first option to install the `code` command in your PATH.

{{< figure src="images/courses/cs9/unit00/-000_initialsetup6.png" width="75%" alt-text="mwc setup" >}}

---

## Opening the Terminal

For most of the remaining setup, you will be using your `Terminal`. This is an application that lets you type commands directly to your computer. You can access it through any of these ways:

- Using your `🔍 spotlight search` (press `⌘`+`space` then type "terminal")
{{< figure src="images/courses/cs9/unit00/-000_initialsetup9.png" width="75%" alt-text="mwc setup" >}}

- Or, you can find it using your computer's `launchpad`
{{< figure src="images/courses/cs9/unit00/-000_initialsetup11.png" height="25%" alt-text="mwc setup" >}}


One you have it open, it should look something like this:
{{< figure src="images/courses/cs9/unit00/-000_initialsetup10.png" width="50%" alt-text="mwc setup" >}}

---
 
## Installing Xcode

{{< code-action "Copy and paste the command below into your Terminal to install Xcode." >}} Then press `Enter/Return`. Make sure you have a strong internet connection, this may take up to 2 hours to complete. Don't worry, you can still use your computer and have it running in the background. 

```shell
xcode-select --install
```


{{< code-action "Enter your password when prompted." >}} You won't see any letters appearing as you enter the password. This is a security feature.

{{< aside >}}
If you already have this installed, you will see the following message instead:
```shell
xcode-select: error: command line tools are already installed, use "Software Update" to install updates
```
{{</ aside >}}

---

## Installing Python
*Python is the language we will be coding in*

(0) **Start by installing the latest version of Python.** [Open this link](https://www.python.org/downloads/), click "Download Python," and follow the installation instructions.


(1) **Once the installation finishes, you will see a Finder window showing what was installed**.
(If you closed the window, open Finder, click on "Applications," and then "Python 3.12" (or whatever version of Python you just installed).


(2) **Check Python installed successfully by typing `python --version` into the Terminal.** You should see a version number above `3.12`.

(3) **Double-click on "Install Certificates.command".** This will will open a Terminal window and run a bunch of commands. Once you see `[Process completed]`, you may close the window.

(4) **Double-click on "Update Shell Profile.command".** Each of these will open a Terminal window and run a bunch of commands. Once you see `[Process completed]`, you may close the window.

[Here is a video that walks you through the steps.](https://youtu.be/OiCiOgeyaWA)


{{< aside >}}
**If you see a red "Permission denied" error message when running "Install Certificates.command"**:
- open a Terminal window and run **`sudo "/Applications/Python 3.12/Install Certificates.command"`**
- You will be asked for an administrator password; you won't see any letters appearing as you enter the password. This is a security feature.
{{</ aside >}}

<!-- {{< youtube "OiCiOgeyaWA" >}} -->

---

## Installing Homebrew
*Homebrew helps you install different libraries and packages*

{{< code-action "Run the below command to install homebrew." >}} This will install homebrew onto your computer. This may take up to an hour to complete. Don't worry, you can still use your computer and have it running in the background. If you already have homebrew, then this step will be quick.

```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

💻 **As the installation runs, follow all the instructions, such as:**

**1. Type your password** - you won't see any letters appearing as you enter the password. This is a security feature.

{{< figure src="images/courses/cs9/unit00/-000_initialsetup13.png" width="50%" alt-text="mwc setup" >}}


**2. Press `return` to continue** 

{{< figure src="images/courses/cs9/unit00/-000_initialsetup14.png" width="50%" alt-text="mwc setup" >}}

**It may ask you to press `Enter` a few more times throughout the process.**

You will know it is finished when you see your username and a `$` once again. For example:*
```shell
bgenzlinger~/Documents$
```

---


## Installing Poetry
*Poetry makes sure your coding environment is set up to work for all your coding projects*

{{< code-action "Run the below command to install Pipx with Brew." >}} 
```shell
brew install pipx
```

{{< code-action "Run the below command to install Poetry." >}} 
```shell
pipx install poetry
```

---

<!-- {{< code-action "Run the below command to install the Github CLI." >}}
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

{{< code-action "When prompted, copy your code and press enter." >}} Then you can follow the prompts in your browser. -->


<!-- 
## If you are using Windows, please email your teachers as soon as possible and they will send you updated instructions. --> 
<!-- ## Install Linux

## Installing Python

(0) **Start by installing the latest version of Python.** [Open this link](https://www.python.org/downloads/), click "Download Python," and follow the installation instructions.
  - Make sure you select `Add Python 3.10 to PATH'

(1) **Open Windows Powershell**. We will be using this application every class. We suggest you pin it to your toolbar.
{{< figure src="https://upload.wikimedia.org/wikipedia/commons/a/af/PowerShell_Core_6.0_icon.png" width="25%" alt-text="Python Turtle Graphics" >}}

(2) **Check Python installed successfully by typing `python --version` into Powershell.**
> You should see a version number above `3.10`

{{< youtube "uhRWvk1Cafc" >}}


## Installing Github for CLI

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


{{< aside >}}
Whenever this website says to use Terminal, you should use Windows Powershell. There will be other small differences for Windows users that we'll explain along the way.
{{< /aside >}} -->


## Testing your Setup



💻 **Run each of the following checks one at a time to check your setup.**


```shell
code -v
```

```shell
xcode-select --install
```

```shell
python3 --version
```

```shell
brew --version
```

```shell
poetry --version
```

📸 **Take a screenshot** of the result and send it to your teachers, *bgenzlinger@isf.edu.hk* and *eqbrown@isf.edu.hk*, regardless of whether it worked or not. 

A successful setup will look something like this:

{{< figure src="images/courses/cs9/unit00/-000_initialsetup15.png" width="100%" alt-text="mwc setup" >}}