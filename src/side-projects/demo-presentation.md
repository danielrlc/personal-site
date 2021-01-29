---
title: Phrase Learner
layout: layouts/base.njk
---

# Brief introduction to Langapp

## A prototype app for language learners

### By Daniel Clarke

#### 25th January 2021

---

### (Start your stopwatch, Daniel)

---

## What it is

Langapp helps English learners learn texts and phrases quickly.

## How it works

Text (eg dialogue) => App code => flexible learning material

---

# Two Langapp iterations

We will look at two iterations of the app.

- **Iteration #1: Lingofin** - UX
- **Iteration #2: Phrase Learner** - UX and code

---

# Iteration #1: Lingofin

- Built in early 2020
- Built with [Gatsby](https://www.gatsbyjs.com/) and [Tailwind CSS](https://tailwindcss.com/)
- [Demo](https://lingofin.netlify.app)
- [Source code on Gitlab](https://gitlab.com/danielrlc/lingofin)

---

# Let's take a look

### [Remote work and social distancing | Lingofin](https://lingofin.netlify.app/01/01-remote-work-and-social-distancing)

---

# Lingofin UX: The Good... 1/2

Lingofin puts **you**, the learner, in charge. It doesn't make decisions for you.

- **You** choose how you learn each word and phrase.
- **You** decide exactly when you've learnt a word or phrase.

---

# Lingofin UX: The Good... 2/2

- Breadcrumbs help with navigation
- Mobile-first, but designed for all sizes of screen
- Text and buttons are locked in position
- Buttons are faded out when inactive

---

# Lingofin UX: The Okay...

- The UI is cluttered, but tells you what you've learnt so far.

---

# Lingofin UX: The Workarounds...

- The app is deliberately slightly taller than fullscreen on mobile. This is so you can remove the chrome in the Chrome and Safari mobile browsers by scrolling down.
- (This needs a real mobile device to demonstrate.)

---

# Lingofin UX: The "Needs to be fixed"

- Too many phrases (up to 100) per exercise
- The button texts could be clearer.
- The app is not beginner friendly. I (selfishly?) optimised it for myself, an advanced user.
- That cluttered UI!

---

# Iteration #2: Phrase Learner

- I started building this a few days ago, so it's a work in progress.
- Built with [Stimulus](https://stimulus.hotwire.dev/) and [Tailwind CSS](https://tailwindcss.com/)
- [Source code on GitHub](https://github.com/danielrlc/tec-stimulus)

---

# Phrase Learner: UX improvements (so far)

- Clearly labelled buttons
- A single hints button (rather than two)
- A decluttered UI

---

# Phrase Learner: Upcoming UX improvements

- A separate screen to view which phrases you've learnt already
- Progressive enhancement: The text will be displayed by default when the page loads. JavaScript can then add the interactivity.

---

# Why Stimulus?

- Very simple and minimal
- No dependencies
- Leads to very explicit HTML code, with clear separation between element attributes for CSS and JavaScript
- Built and maintained by contributors with a long and excellent track record in open-source software

---

# Why Tailwind CSS?

- "Rapidly build modern websites without ever leaving your HTML."
- It helps you avoid [specificity wars](https://csswizardry.com/2014/10/the-specificity-graph/) in your CSS.
- It helps you avoid [premature abstraction](https://tailwindcss.com/docs/extracting-components).
- It takes away naming headaches, by providing structured naming for almost everything you need.

---

# Simple, explicit code is the goal

---

# Stimulus style guide enforced by Prettier

```javascript
// Prettier config file forces "no semicolons" style
this.buildPhrase();
```

---

# Naming 1/2

```javascript
// actions start with a verb
buildPhrase();
flipHints();
renderView();

// booleans are a verifiable statement
hintsAreShown = true;
allWordsAreShown = false;
```

---

# Naming 2/2

```javascript
// Longer names are used when needed
checkIfAllWordsAreShown()

// Larger tasks are split into clearly named methods
renderView() {
  this.checkIfAllWordsAreShown()
  this.renderPhraseText()
  this.renderButtons()
}
```

---

# State and view kept separate

```javascript
flipHints() {
  this.hintsAreShown = !this.hintsAreShown
  this.renderView()
}

renderView() {...}
```

---

# Explicit HTML, thanks to Stimulus

```html
<!--
click = listening for click event
phrase-flip-exercise = name of Stimulus controller
flipHints = name of action method to take on click
-->
<button data-action="click->phrase-flip-exercise#flipHints">...</button>
```

---

# Fast prototyping with Tailwind

Quickly add and edit Tailwind utility classes right inside your HTML.

```html
<button
  class="text-sm px-3 py-1 mx-1 my-2 bg-gray-200 hover:bg-gray-300 rounded"
></button>
```

---

# Reusing styles in Tailwind

But what about reuse? This would break DRY principles:

```html
<button class="text-sm px-3 8-more-classes..."></button>
<button class="text-sm px-3 8-more-classes..."></button>
<button class="text-sm px-3 8-more-classes..."></button>
```

---

# Create a Tailwind component

```css
/* css */
.btn-gray {
  @apply text-sm px-3 8-more-classes /* ... */;
}
```

```html
<!-- html -->
<button class="btn-gray">...</button>
<button class="btn-gray">...</button>
<button class="btn-gray">...</button>
```

---

# Thanks for listening!

- Phrase Learner demo online?
- Slides for talk?
