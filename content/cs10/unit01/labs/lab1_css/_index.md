---
title: "1: CSS"
weight: 10
draft: true
---

# CSS Lab

In this lab, you will start learning to write `CSS` code!

---

## [0] Set up

We are now in the **Web Design** unit, so you'll need to make a new folder. 

{{< code-action  >}} **In the Terminal, go into your `making_with_code/cs10` folder and create a `unit01_webdesign` folder.**

```shell
cd ~/desktop/making_with_code/cs10
mkdir unit01_webdesign
```


{{< code-action "Then, clone your starter code." >}} Be sure to change `yourgithubusername` to your actual Github username.
```shell
git clone https://github.com/the-isf-academy/lab_html_yourgithubusername
cd lab_html_yourgithubusername
```

{{< code-action >}} `cd` **into the lab**
```shell
cd lab_html_yourgithubusername
```

{{< aside "No need for the Poetry shell" >}}

In this unit we will not be using Python, and so **we will NOT use the Poetry shell**.

Don't worry, we'll return to Python in the next unit - Web Apps :)

{{< /aside>}}



---



## [1] Flexbox Guide

The `display: flex` property is an incredibly useful `CSS` property to apply flexible and layouts. You can see an example of this in the `flexbox_example` folder. 

### Equally Sized Columns

Often times we want content to be side-by-side. We can use a flexbox layout to achieve this. 

{{< figure src="images/courses/cs10/unit01/01_css_0.png" width="100%" >}}

{{< code-action >}} **This is the `html` for multiple columns.** 

```html
<div class="flexbox-grid">
  <div class="column">
    <h2>column</h2>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse luctus dapibus consequat. Duis congue scelerisque odio eu suscipit. Nunc at ligula non libero viverra dapibus. In sit amet lacinia odio.</p>
  </div>

  <div class="column">
    <h2>column</h2>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse luctus dapibus consequat. Duis congue scelerisque odio eu suscipit. Nunc at ligula non libero viverra dapibus. In sit amet lacinia odio.</p>
  </div>
</div>
```

{{< code-action >}} **This is the `css` for the two classes: `flexbox-grid` and `column` grid.** 

```css
.flexbox-grid{
    display:flex;
    gap: 20px;
    margin-bottom: 50px;
}

.column{
    background-color: rgb(255, 243, 203);
    padding: 0px 20px;
    flex: 1;
}
```


### Unevenly sized columns


### Responsive Design: Mobile Friendly 


## [2] Deliverables

{{< deliverables "Once you've successfully completed the lab:" >}}  


☑️  **Fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSe-mGrk41m6_-iZtqw5X1LpmYrfhF68Kbw8XJBCNv0XsqHG-Q/viewform?usp=sf_link)**

{{< code-action "Push your code to Github." >}}
- git status
- git add -A
- git status
- git commit -m "describe your code and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}

--- 

## [3] Extension: CSS 
