<script>
//@ts-nocheck
// import {onMount} from '$lib/util';
export let items;
export let slideExtra = [];
export let theme;

/////////////////////////////////////////////////

</script>

<div class="flex flex-col justify-center p-2 mx-4 my-0 text-center">
    <h1
    class='p-1 m-1'
     style = {`
            color: ${theme.secondaryColor};
        `}
    >Message</h1>
 
        <textarea  rows="10"
        bind:value={items[0].content}
        class=" rounded-md p-1   w-full border-2 text-center" 
         style = {`
            color: ${theme.textColor};
            background-color: ${theme.backgroundColor};
            border-color: ${theme.secondaryColor};
        `}
          />
        
      
</div> 

<!-- <button on:click={()=>console.log(slide)}>dump</button> -->


    