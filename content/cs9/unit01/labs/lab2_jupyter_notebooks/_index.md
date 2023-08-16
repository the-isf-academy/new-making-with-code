---
title: 2. Jupyter Notebook
type: checkup
# draft: True
---
# Jupyter Notebooks

In this mini-lab we will be introducing a new tool, Jupyter Notebook.

## [0] Jupyter, what?

Jupyter Notebook is a special kind of programming environment that lets you write and run snippets of code in the same interface. This interface is a powerful tool for data science because it allows you to work on Python scripts in finer detail. This will help you clean, analyze, and visualize data without having to re-run entire Python scripts.

{{< figure src="images/courses/cs9/unit01/01_sumstats_jupyter.gif" width="100%" title="Opening a Jupyter Notebook" >}}


### [Setup Jupyter Notebook]

{{< code-action "Let's start by installing and setting up" >}} `Jupyter` **on your computer:**

{{< tabs "jupyter-setup" >}}
{{< tab "MacOS" >}}
```shell
bash <(curl -sL https://raw.githubusercontent.com/the-isf-academy/courseware/master/cs9_student_setup/setup_jupyter.sh)
```

{{< /tab >}}
{{< tab "Windows" >}}

You can install Jupyter using pip in Ubuntu:

    $ sudo apt update
    $ sudo apt install python3-pip
    $ pip3 install --upgrade pip
    $ pip3 install --upgrade --user -r requirements.txt
    $ vim ~/.bashrc

Inside bashrc, scroll to the very end of the document. Press `I`.
Then add:

    alias jupyter-notebook="~/.local/bin/jupyter-notebook --no-browser"

Once completed, press `ESC` button.

    $ source ~/.bashrc

Now, install some extensions to make your notebooks nicer:

    $ jupyter-notebook  nbextension enable toc2/main && jupyter-notebook nbextension enable collapsible_headings/main && jupyter-notebook nbextension enable hide_input/main && jupyter-notebook nbextension enable varInspector/main && jupyter-notebook nbextension enable hinterland/hinterland && jupyter-notebook nbextension enable python-markdown/main && jupyter-notebook nbextension enable spellchecker/main && jupyter-notebook nbextension enable exercise2/main

{{< /tab >}}
{{< /tabs >}}


## [1] Using Jupyter Notebook

### [Code Repo]

As always, we'll start by cloning your lab repo from Github.

{{< code-action >}} **Start by cloning your `lab-jupyter` repository in your `cs9` folder.**
```shell
cd desktop/cs9/unit_01
git clone https://github.com/the-isf-academy/lab-jupyter-YOUR-GITHUB-USERNAME.git
```

{{< code-action >}} **`cd` into your lab directory (`cd lab-jupyter-USERNAME`) and you'll notice a new type of file: `.ipynb`.** These files are used with Jupyter notebook. The best way to understand Jupyter is just to try it out.

{{< code-action "Type" >}} **`jupyter notebook` in your terminal.** This will start a Jupyter server in your terminal. Your web browser should automatically open.
> If this does not work, try **`jupyter-notebook`**

{{< code-action "In the web browser window that pops up, click on the file" >}} `jupyter_intro.ipynb`.

{{< code-action "Walk through the intro to learn how to use Jupyter." >}} 