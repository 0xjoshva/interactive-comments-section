<template>
  <router-view/>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@100;200;300;400;500;600;700;800;900&family=Rubik:wght@300;400;500;600;700;800;900&display=swap');
/* font-family: 'Rubik', sans-serif; */
*, *::before, *::after {
  box-sizing: border-box;
}
* {
  margin: 0;
}
html, body {
  height: 100%;
  font-family: 'Rubik', sans-serif;
}
body {
  line-height: 1.5;
  -webkit-font-smoothing: antialiased;
  background-color: hsl(228, 33%, 97%);
}
img, picture, video, canvas, svg {
  display: block;
  max-width: 100%;
}
input, button, textarea, select {
  font: inherit;
}
p, h1, h2, h3, h4, h5, h6 {
  overflow-wrap: break-word;
}
#root, #__next {
  isolation: isolate;
}
:root {
  /*Primary */
  --Moderateblue: hsl(238, 40%, 52%);
  --SoftRed: hsl(358, 79%, 66%);
  --Lightgrayishblue: hsl(239, 57%, 85%);
  --Palered: hsl(357, 100%, 86%);

  /* Neutral */
  --Darkblue: hsl(212, 24%, 26%);
  --GrayishBlue: hsl(211, 10%, 45%);
  --Lightgray: hsl(223, 19%, 93%);
  --Verylightgray: hsl(228, 33%, 97%);
  --White: hsl(0, 0%, 100%);
}
</style>
