---
title: "2: Responsive Design"
weight: 10
# draft: true
---


# Responsive Design 

In this lab, you will learn how to differentiate CSS for mobile viewing and continue exploring CSS design properties. 

---

## [0] Set up



{{< code-action "Start by cloning your starter code." >}} Be sure to change `yourgithubusername` to your actual Github username.
```shell
cd ~/desktop/making_with_code/cs10/unit01_webdesign
git clone https://github.com/the-isf-academy/lab_responsive_design
```

{{< code-action >}} `cd` **into the lab**
```shell
cd lab_responsive_design_yourgithubusername
```

📄 **This repo contains the following:**
- `index.html`
- `styles.css`
- `assets/` - contains 1 images
- `README.md`

{{< code-action >}} Start by openning the repo in VS code and opening the `index.html` page
```shell
code .
open index.html
```

{{< figure src="images/courses/cs10/unit01/02_responsive_8.png" width="75%" >}}


---

## [0] Mobile Queries

{{< code-action >}} **Let's start by opening the `Inspect` tool so we can view the site on mobile.** As you can see, the content on the site does not get adjusted for the phone. The buttons are no longer visible and some of the text is mis-aligned. 
> Click the computer/phone icon to switch to mobile mode

{{< figure src="images/courses/cs10/unit01/02_responsive_0.png" width="25%" >}}

👀 **This is what the site would look like on an iPhone 12 Pro.** 
> Try changing the dimension settings by clicking on the drop down.

{{< figure src="images/courses/cs10/unit01/02_responsive_1.png" width="50%" >}}

💻 **Let's start by looking at the media query at the bottom of the `styles.css` file.** 
> Media queries change the CSS properties for specific screen sizes - *learn more [here](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries)*

```css
* FOR MOBILE SCREEN SIZE */

@media only screen and (min-width: 375px) and (max-width: 767px)
{
    .container {
        display: flex;
        margin-top: 0px;
    }
}
```

💻 **Let's change our `display` property to `block` instead of `flex`, so the content to stack on top of each other, instead of side by side.** It's looking better!

{{< figure src="images/courses/cs10/unit01/02_responsive_3.png" width="25%" >}}


💻 **Now, it's up to you to edit the exisitng CSS rules and add more specific CSS rules in the media query!** Try to match the screenshots below. 
> *Don't forget to scroll to the bottom and check the 'back to the top' text*

{{< columns >}}
{{< figure src="images/courses/cs10/unit01/02_responsive_2.png" width="50%" >}}
<--->
{{< figure src="images/courses/cs10/unit01/02_responsive_4.png" width="75%" >}}

{{< /columns >}}


---

## [1] Customizing the Site

Now that the mobile looks better, let's improve the site!

---

### [Internal Links]

You can link to an internal part of your site by setting an `id` to an `HTML` element. 

💻 **Try clicking on the `activites` link.** It jumps you to the activites section of the page. But, the `contact me!` and `meow` buttons are broken. 

{{< figure src="images/courses/cs10/unit01/02_responsive_5.png" width="25%" >}}

📖 **This is the `HTML` code for the link. It's `href` points to the `id` of the about section.**

```html
<a class="border-box" href="#about">activites</a>
```

📖 **This is the `HTML` code for the `<h2>` section heading.**

```html
<h2 id="about">about</h2>
```

💻 **Fix the links for the `contact me!` and `meow` buttons so they jump you to the correct part of the site.**

---

### [Gradients]

💻 **Experiment with CSS graidents at [cssgradient.io](https://cssgradient.io/)**


💻 **When you find one you like, copy the `linear-gradient`**

{{< figure src="images/courses/cs10/unit01/02_responsive_6.png" width="75%" >}}

💻 **Paste it into the top of your `styles.css` and replace the current `--bg-graident` value**
> *These are `CSS` variables, which allow you to more quickly retheme your site - learn more [here](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)*
```css
:root {
    --bg-gradient: radial-gradient(circle, rgba(44,55,111,1) 46%, rgba(87,26,70,1) 100%);
    --border-gradient: linear-gradient(to right, rgb(193, 193, 237), rgb(234, 193, 255)) 1;
    --color1: white;
    --color2: rgb(67, 77, 131);
    --color3: rgb(93, 102, 148);
}
```

💻 **Experiment with the other variables and change the theme to *light mode*.**

{{< figure src="images/courses/cs10/unit01/02_responsive_7.png" width="75%" >}}




## [2] Deliverables

{{< deliverables "Once you've successfully completed the lab:" >}}  


{{< code-action "Push your code to Github." >}}
- git status
- git add -A
- git status
- git commit -m "describe your code and your process here"
  > be sure to customize this message, do not copy and paste this line
- git push

{{< /deliverables >}}



## [3] Extension: CSS  

💻 **Experiment with UX/UI design by customizing this site!** This is the last practice lab before your make your own site, so us this as opportunity to test ideas. 

