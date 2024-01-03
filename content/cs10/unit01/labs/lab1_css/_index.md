---
title: "1: CSS"
weight: 10
# draft: true
---

<style>
.flexbox-grid{
    display:flex;
    gap: 20px; 
}

.column{
    background-color: rgb(255, 243, 203);
    padding: 0px 20px;
    flex: 1;
}


#col-large{
    background-color: rgb(255, 216, 216);
    flex-grow: 3; 
}



/* FOR MOBILE SCREEN SIZE */

@media only screen and (max-width: 768px) {


    .flexbox-grid {
        display: block;
      }

    .column{
        margin: 10px;
        padding: 10px 10px; 
    }

}
</style>


# CSS Lab

In this lab, you will start learning to write `CSS` code! CSS defines the design style and layout of web site.


---

## [0] Set up



{{< code-action "Start by cloning your starter code." >}} Be sure to change `yourgithubusername` to your actual Github username.
```shell
cd ~/desktop/making_with_code/cs10/unit01_webdesign
git clone https://github.com/the-isf-academy/lab_css_yourgithubusername
cd lab_css_yourgithubusername
```

{{< code-action >}} `cd` **into the lab**
```shell
cd lab_html_yourgithubusername
```


---

## [0] Wireframe Design

The `/amusement` and `/weather` directories are different contexts students will design for and contains an HTML document
with information for that contexts.

Here are the provided contexts:
- [Weather Alert](weather/)
- [Amusement Park](amusement/)


✏️ **First, complete the design worksheet.** 


💻 **Second, exchange design documents and implement your partners design in `HTML` and `CSS`.** This will require you to write `CSS` rules for various HTML elements. You may even want to implement `class` and `id` selectors for layout components and finer tuning of aesthetic design. 

---


## [1] Flexbox Guide

💡 **The `display: flex` property is an incredibly useful `CSS` property to apply flexible and layouts.** It can be used to create responsive layouts and side-by-side content. 

📖 **Here are two helpful resources for using a `flexbox`**
- [flexbox guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [flexbox grid tutorial](https://kevinsguides.com/guides/webdev/css/creating-a-simple-flexbox-grid)

---

### [Equally Sized Columns]

**We often want content size-by-side in two equally sized columns.**

> 💻 *Try resizing the browser window - notice how the boxes are *responsive* and resize and rearrange depending on the screen size.*
>
> *The background color is not required - it is just used here to illustrate the different columns*

<div class="flexbox-grid" >
  <div class="column"">
    <h3>column</h3>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
  </div>

  <div class="column" >
    <h3>column</h3>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. </p>
  </div>
</div>


👀 **This is the `html` code for the columns above.** 

```html
<div class="flexbox-grid" >
  <div class="column"">
    <h3>column</h3>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
  </div>

  <div class="column" >
    <h3>column</h3>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. </p>
  </div>
</div>
```

👀 **This is the `css` for the two classes: `flexbox-grid` and `column` grid.** 

```css
.flexbox-grid{
    display: flex;
    gap: 20px; 
}

.column{
    background-color: rgb(255, 243, 203);
    padding: 0px 20px;
    flex: 1;
}
```
> - `.` - is used to apply rules to a `CSS Class`
- = **`flex`** - this makes each column equal in size


---


### [Unevenly Sized Columns]

**What if we want content size-by-side in two un-equally sized columns?**

> 💻 *Try resizing the browser window - notice how the boxes are *responsive* and maintain the relative size ratio. They also stack if the window is too small.*
>
> *The background colors are not required - it is just used here to illustrate the different columns*

<div class="flexbox-grid">
  <div class="column">
    <h3>column 1</h3>
    <p>Suspendisse luctus dapibus consequat.</p>
  </div>

  <div class="column" id="col-large">
    <h3>column 3</h3>
    <p>Vivamus pellentesque molestie odio, eu porttitor dui pharetra id. Nunc tempus tristique tortor, sit amet pellentesque magna accumsan sed. Nullam posuere nunc eu libero rutrum sodales. Duis congue scelerisque odio eu suscipit. Nunc at ligula non libero viverra dapibus. In sit amet lacinia odio.</p>
  </div>
</div>

👀 **This is the `html` code for the columns above.** 

```html
<div class="flexbox-grid">
  <div class="column">
    <h3>column 1</h3>
    <p>Suspendisse luctus dapibus consequat.</p>
  </div>

  <div class="column" id="col-large">
    <h3>column 2</h3>
    <p>Vivamus pellentesque molestie odio, eu porttitor dui pharetra id. Nunc tempus tristique tortor, sit amet pellentesque magna accumsan sed. Nullam posuere nunc eu libero rutrum sodales. Duis congue scelerisque odio eu suscipit. Nunc at ligula non libero viverra dapibus. In sit amet lacinia odio.</p>
  </div>
</div>
```

👀 **This is the `css` for the two classes: `flexbox-grid` and `column` grid.** *Notice, it uses two of the same `CSS classes`, `flexbox-grid` and `columns` and the example above.*

```css
.flexbox-grid{
    display:flex;
    gap: 20px; 
}

.column{
    background-color: rgb(255, 243, 203);
    padding: 0px 20px;
    flex: 1;
}

#col-large{
    background-color: rgb(255, 216, 216);
    flex-grow: 3; 
}
```
> - `#` - is used to apply rules to a `CSS ID`
> - **`flex-grow`** - this makes `col-2` 3x as big

---


### [Responsive Design: Mobile Friendly]

📱**It is important for websites to be viewable and readable on different sized screens - like on a phone**. 

👀 **This is the `css` applied to the `divs` in the two examples.** 

```css
/* FOR MOBILE SCREEN SIZE */

@media only screen and (max-width: 768px) {

    .flexbox-grid {
        display: block;
      }

    .column{
        margin: 10px;
        padding: 10px 10px; 
    }

}
```
> - **`@media only screen and (max-width: 768px)`** - this applies different `CSS` properties for the two classes, `flexbox-grid` and `column`, when the window is at a specific screen size
- `/* FOR MOBILE SCREEN SIZE */` - is a comment, just like the `#` for comments in Python 
  - You can learn more about `media queries` [HERE](https://www.w3schools.com/css/css_rwd_mediaqueries.asp).


---

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
