# Sass Note

## Environment Set Up

Step1:

npm install node-sass

npm init -y \(skip writing descriptions and initialize package.json\)

npm install node-sass

Step2: \(change a line of code in package.json \)

"scripts": {

  "sass":  node-sass -w scss/ -o  dist/css/ --recursive

}

Step3: create a file path called scss and put a file main.scss inside and also create a file path called dist and put css folder inside

in the terminal : npm run sass

if successful, whatever written inside main.scss will be converted into css.

Step4:  link css with html inside of head

&lt;link rel="stylesheet" href="css/main.css" /&gt; 

ps: dist contains css folder and index.html

## Variables:

put all of variables into \_variables.scss file to avoid file auto conversion

define variables:

```css
$primary-color: steelblue;
$secondary-color: skyblue;
$light-color: #f4f4f4;
$dark-color:#333;
$font-stack: Arial, Helvetica, sans-serif;


```

## Functions:

put all of functions into \_functions.scss file to avoid file auto conversion

```css
// Set Text Color

@function set-text-color($color) {
  @if(lightness($color) > 50) {
    @return #000;
  } @else {
    @return #fff;
  }
}
//Transform minxin
@mixin transform($property) {
  --webkit-transform: $property;
  --ms-transform:$property;
  transform: $property;
}

```

## main.scss

```css
@import 'variables';
@import 'functions';

* {
  margin: 0;
  padding: 0; 
}

body {
  background:$light-color;
  color:$dark-color;
  font-family: $font-stack;
  line-height: 1.5; 
}

header{
  background: $dark-color;
  color: set-text-color($dark-color);
  padding: 1rem;

  h1 {
    text-align:center;
  }
}

.section {
  padding: 3rem;

  h3 {
    font-size: 2rem;
  }

  &-a {
    background: $primary-color;
    color:#fff;
  }

  &-b {
    background: $secondary-color;
    color:#fff;
  }
}

// & means parent
a {
  color:#333;
  &:hover { 
    color: coral;
  }
}


// inheritance 
%btn-shared {
  display: inline-block;
  padding: 0.7rem 2rem;
  border: none;
  cursor: pointer;
  text-decoration: none;
  margin-top:1rem;
}

.btn {
  &-light {
    @extend %btn-shared;
    background-color: $light-color;
    color:#333;
    
    // the way to use function
    &:hover {
      @include transform(rotate(20deg));
      background-color:darken($light-color, 10%);
    }
  }

  &-dark {
    @extend %btn-shared;
    background-color: $dark-color;
    color:#fff;

    &:hover {
      @include transform(rotate(-20deg));
      background-color:darken($light-color, 10%);
    }
  }
  
}


```





