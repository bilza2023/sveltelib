<script>
  import { onMount } from "svelte";
  import {
    Presentation,
    themes,
    ThemeDD,
    getNewSlide,
    getNewItem,
  } from "../lib/Presentation/index.js";

  import PContiner from "../lib/Presentation/PContainer.svelte";
  import { fade } from "svelte/transition";
  import Toolbar from "./Toolbar.svelte";


  const currentSlide = getNewSlide();

  currentSlide.items.push(getNewItem());
  currentSlide.items.push(getNewItem());
  currentSlide.items[0].content = "This is the Heading";
  currentSlide.items[1].content =
    "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed ut fringilla eros. In hac habitasse platea dictumst. Integer sed arcu.";

  currentSlide.type = "HdgPara";
  currentSlide.endTime = 200;

  let screenWidth;
  let screenHeight;
  let fontSize = "80px";

  console.log("screenHeight", screenHeight);

  function setPulse() {
    console.log("setPulse");
  }
  let pulse = 0;
  let theme = themes.basic;
  /////////////////////////////////////////////////////////////
  theme.backgroundColor = "gray";

  /////////////////////////////////////////////////////////////
  // default :{
  //     description     : '',
  //     primaryColor    : '#BC6C25',
  //     secondaryColor  : '#DDA15E',
  //     backgroundColor : '#FEFAE0',
  //     textColor       : '#283618',
  //     highlightColor  : '#606C38',
  // };
  /////////////////////////////////////////////////////////////
  let toolbarVisible = false;

  let timeout;

  function handleMouseMove() {
    console.log("okk");
    toolbarVisible = true;
    clearTimeout(timeout);
    // setToolbarVisibility(true);
    timeout = setTimeout(() => {
      toolbarVisible = false;
      console.log("fired!!!!!!!!!!!!!!!!");
    }, 2000); // 5 seconds
  }

  function adjustFontSize() {
  const heading = document.getElementById("heading");
  let currentFontSize = parseFloat(getComputedStyle(heading).fontSize);
  let currentHeight = heading.clientHeight;
  const quarterScreenHeight = screenHeight * 0.20;

  while (currentHeight < quarterScreenHeight) {
    currentFontSize++;
    heading.style.fontSize = `${currentFontSize}px`;
    currentHeight = heading.clientHeight;
  }
}

// Inside the onMount hook
onMount(() => {
  screenWidth = window.innerWidth;
  screenHeight = window.innerHeight;
  toolbarVisible = false;
  adjustFontSize();
});

let fontSize2 = "40px"

</script>

<!-- svelte-ignore a11y-no-static-element-interactions -->
<div on:mousemove={handleMouseMove}>
  <div class="outerContainer ">
    {#if toolbarVisible}
      <div in:fade={{ delay: 100 }} out:fade={{ delay: 500 }}>
        <Toolbar />
      </div>
    {/if}
   

  <!-- <h1 id="heading" class="mx-auto"
  style={`font-size: ${fontSize}; top:50px;`}
  >This is 25% of the Height</h1>

  <div id="para" class="mx-auto" style={`font-size: ${(fontSize2 )}; top:200px;`}>This is the text.This is the text.This is the text.This is the text.This is the text.This is the text.This is the text.This is the text.</div> -->
    
    <Presentation {currentSlide} {theme} {pulse} {setPulse} tcode={"fbise9math"}/>
  </div>
</div>

<style>
  .outerContainer {
    min-width: 100vw; /* 100% of the viewport width */
    min-height: 100vh; /* 100% of the viewport height */
    background-color: rgb(37, 27, 15);
  }

  #heading {
    position: absolute;
    left: 0;
    right: 0;
    margin-left: auto;
    margin-right: auto;
    margin-left: 35px;
    margin-right: 35px;
    border-radius: 10px;
    color:  rgb(49, 28, 3);
    background-color: rgb(182, 162, 137);
    white-space: normal;
    text-align: center;
  }

  #para {
    position: absolute;
    left: 0;
    right: 0;
    margin-left: auto;
    margin-right: auto;
    background-color: rgb(182, 162, 137);
    margin-left: 35px;
    margin-right: 35px;
    border-radius: 10px;
    opacity: 1;
    line-height:2em ;
    padding :6px;
    text-align: center;
  }
  
</style>
