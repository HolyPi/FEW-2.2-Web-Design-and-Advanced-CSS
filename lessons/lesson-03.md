# FEW 2.2 - Advanced CSS - SASS

Not Special Array Storage System...

CSS Preprocessors: SASS - Syntactically Awesome StyleSheets. 

## Why you should know this?

CSS preprocessors are common in industry and provide some valuable functionality. Expect to see them in the work flow of companies large and small.

## Learning Objectives

1. Define CSS preprocessor functionality and uses cases
1. Write code in the scss language
1. Compile code written in scss to vanilla CSS

## What is SASS? 

**Q:** What is SASS? 
**A:** SASS is a language that compiles to vanilla CSS. 

**Q:** Why use SASS? 
**A:** SASS provides a way to generate CSS from higher level code that inlcudes variables, conditional statements, loops, and more. These are things that _don't exist in vanilla CSS_. 

**Q:** Can I use the SASS language in the browser?
**A:** No, you must compile scss to CSS first. 

**Q:** How do you compile SASS? 
**A:** Use a preprocessor, there are a few to choose from. Both command line tools and desktop applications. 

## Install SASS

There are several tools you can use to compile SASS.

- http://koala-app.com
- http://compass-style.org
- SASS CLI

You will use Node JS version since you have been using Node for other projects. 

Install Node SASS.

`npm install -g sass`

## Compiling SASS

Compile SASS.

1. Make a new folder
1. Create `index.html`
  - add a link to `styles.css` - `<link rel="stylesheet" href="styles.css">`
1. Create `style.scss`
1. Run SASS from the command line: `sass --watch style.scss style.css`

The last line above runs SASS. The `--watch` flag tells SASS to watch for changes and update when it sees them. The last two parameters: `style.scss style.css` define the input (`style.scss`) and output (`style.css`) files.

The setup above will watch for changes in `styles.scss` and upon seeing them compile the scss code there into regular css in `style.css`.

Try it. 

## Getting started with SASS

SASS supports variables. Use it to: 

- Share values for DRY code
- Calculate relative values for DRY code 
- Create mixins (like functions) for DRY code
- Use utility functions to help your work

The main use of SASS is to more maintainable CSS code. 

**Variables** in SASS always begin with the `$`

<small style="color: #999">SCSS code</small>
```SCSS
$bg-color: #eee;
$font-color: #333;
$font-size: 16px;
$typical-margin: 0 0 1em 0;
```

Notice variables always begin with the `$`. You can assign any value. This includes any value that is legal CSS. 

Use a variable where any value might appear: 

<small style="color: #999">SCSS code</small>
```SCSS
body {
  background-color: $bg-color;
  color: $font-color;
  font-size: $font-size;
}
```

The code above would compile into: 

<small style="color: #999">CSS code</small>
```CSS
body {
  background-color: #eee;
  color: #333;
  font-size: 16px;
}
```

Use all of those math operators! 

<small style="color: #999">SCSS code</small>
```SCSS
$margin: 16px;
$cols: 4;
$width: 800px;
$col-width: $width / $cols + $margin * 2;
```

**Loops** are directives that begin with `@`. 

<small style="color: #999">SCSS code</small>
```SCSS
@for $i from 1 to 4 {
  .h#{$i} {
    font-size: #{(5 - $i) * 0.85}em;
  }
}
```

<small style="color: #999">CSS code</small>
```CSS
.h1 {
  font-size: 3.4em;
}

.h2 {
  font-size: 2.55em;
}

.h3 {
  font-size: 1.7em;
}
```

Define a list and use an each loop: 

<small style="color: #999">SCSS code</small>
```SCSS
$list: github, twitter, facebook;

@each $icon in $list {
  .photo-#{$icon} {
    background: image-url("images/#{$icon}.png") no-repeat;
  }
}
```

<small style="color: #999">CSS code</small>
```CSS
.photo-github {
  background: image-url("images/github.png") no-repeat;
}

.photo-twitter {
  background: image-url("images/twitter.png") no-repeat;
}

.photo-facebook {
  background: image-url("images/facebook.png") no-repeat;
}
```

There is a lot you can do with this it extends CSS in new ways. _Keep in mind that SASS is always rendered to vanilla CSS!_

## In Class Activity 

Pair up with someone you haven't paired with before. You'll be assigned a topic from the list below. You and your pair are repsonsible for studying and **making an example that explains the concept**. Do you best to think of a practical use for your topic and code sample. 

https://sass-lang.com/documentation

- [Variables](https://sass-lang.com/documentation/variables)
- [Nested Rules](https://sass-lang.com/documentation/style-rules#nesting)
- [Mixins](https://sass-lang.com/documentation/at-rules/mixin)
- [Functions](https://sass-lang.com/documentation/functions)
- [If else](https://sass-lang.com/documentation/at-rules/control/if)
- [For](https://sass-lang.com/documentation/at-rules/control/for)
- [Extend](https://sass-lang.com/documentation/at-rules/extend)

## Typography on Web

CSS provides a few properties to control the appearance of text on the screen. 

- `font-family` - The font face to display
- `font-size` - the size of characters
- `color` - The color of the text
- `line-height` - The of a line of text

Here are strategies for each of these properties. 

**`font-family`** sets the font to use. You're limited to fonts available on any given computer unless you import a custom font. 

Since `font-family` is inherited it's best to set the font-family on body or html tag and all children will share it. 

Usually you'll provide a font stack. This is a list of fonts, the browser will use the first available font on the list. Here is a list of modern font stacks. 

https://gist.github.com/don1138/5761014

**`font-size`** sets the size of the characters. This property is inherited, that means all children will get the `font-size` of their parent. For this reason it's best to set a base font size on the `body` or `html` element. 

Use `em` to set a relative font size of the base font size. 

```CSS
body {
  font-size: 18px;
}

h1 {
  font-size: 2em; /* 36px */
}
```

**`color`** it's color of the text, do we need to say more? Maybe... 

Contrast is important. Low contrast makes things hard to read, especially for people with bad vision. There is a rule you can follow. 

https://webaim.org/resources/contrastchecker/

**`line-height`** the height of a line of text. This doesn't effect size of the characters. Why is `line-height` a thing? Lines that are too close together are harder to read. Usually the default value for `line-height` is too small! 

How do you know what a good line height is? Use your best judgement. Longer lines need larger `line-height`. 

Your goal this week is to apply the ideas above to a project of your own. We will talk more about type in the next class. 

## In Clss Activity

Apply SASS to your CSS drawing and animation. Look for these opportunities: 

- Look for values that can be moved to the top of the code and defined as constants.
- Look for related values that can be calculated rather than written explicitly
- Look for elements that are repeated. Use the two ideas above along with a loop to generate repeated values. 

Review your work with another student before the end of class. 

## Homework 

To really get an understanding for SASS you have to use it. Your goal is to apply SASS to one of your past projects. 

See the description here for details and requirements for this assignment: 

- [Apply SASS to a past project](../Assignments/assignment-03-SASS.md)

## Wrap Up

- Review class 
  - What is SASS?
  - What is good for? 
  - Do you think you would use this? 

## Additional Resources

1. https://sass-lang.com

## Minute-by-Minute [OPTIONAL]

| **Elapsed** | **Time**  | **Activity**              |
| ----------- | --------- | ------------------------- |
| 0:00        | 0:05      | Objectives                |
| 0:05        | 0:15      | Overview                  |
| 0:20        | 0:45      | In Class Activity I       |
| 1:05        | 0:10      | BREAK                     |
| 1:15        | 0:45      | In Class Activity II      |
| TOTAL       | 2:00      |                           |
