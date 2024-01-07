---
title: "1: CSS"
weight: 10
# draft: true
---

<style>

/* FOR CSS INTRO */


h1.css_intro{
  color: pink;
  text-decoration: underline;
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
```

{{< code-action >}} `cd` **into the lab**
```shell
cd lab_html_yourgithubusername
```

📄 **This repo contains the following:**
- `index.html`
- `styles.css`
- `assets/` - contains 5 images
- `README.md`

---

## [0] Wireframe Design

🎨  **In this lab you will design a `wireframe` for the Ocean Park Water Park.** A `wireframe` is a layout design for a website. 


{{< figure src="https://thewebsitearchitect.com/wp-content/uploads/2021/02/How-do-you-draw-a-website-wireframe.jpg" width="40%" >}}



✏️ **First, complete the wireframe design document.** 


💻 **Second, exchange wireframe design documents and implement your partners design in `HTML` and `CSS`.** This will require you to write `CSS` rules for various HTML elements. You may even want to implement `class` and `id` selectors for layout components and finer tuning of aesthetic design. 

---

## [0] CSS Mini-intro

`CSS` allows you define design specifications for `HTML` elements. 

**For example, take this simple example:** `<h1>Hello, World</h1>`

**To change all `<h1>` tags to pink and underlined, all I need to do is write a simple rule in `styles.css`.**

<h1 class="css_intro">Hello, World</h1>



```css
h1{
  color: pink;
  text-decoration: underline;
}
```

💡 **You can write as many *rules* for CSS tags as you need for your design.**

🌐 **There are SO many CSS properties, you do not need to memorize them. Instead,  Google and reference documentation.**
- [w3.css](https://www.w3schools.com/w3css/default.asp)


---

## [2] Deliverables

{{< deliverables "Once you've successfully completed the lab:" >}}  


☑️  **Fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSc00CmVnLI0kyTYSVZ4QeXoimOqUfeot_Ue985K9P2Ih6RgNg/viewform?usp=sf_link)**

{{< code-action "Push your code to Github." >}}
- git status
- git add -A
- git status
- git commit -m "describe your code and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}

<!-- --- 

## [3] Extension: CSS  -->
