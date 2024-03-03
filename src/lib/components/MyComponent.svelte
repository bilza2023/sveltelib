<!-- MyComponent.svelte -->
<script>
    // Any JavaScript logic for your component can go here
   function clk(){console.log("clilcked")} 
  </script>
  
  <button class="my-button" on:click={clk}>Button from Library</button>
  
  <style>
    /* Styles specific to your component */
    .my-button {
      background-color: blue;
      color: white;
      padding: 10px 20px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
  </style>
  