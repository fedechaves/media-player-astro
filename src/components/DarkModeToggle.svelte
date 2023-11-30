<script lang="ts">
    import { onMount } from "svelte";
    let theme = localStorage.getItem("theme") ?? "light";  
    let flag = false;
    onMount(()=>{
      flag = true
    }) 
    $: if (flag) {
      if ( theme === 'dark') {
        document!.documentElement.classList.add("dark");
      } else {
        document!.documentElement.classList.remove("dark");
      }
      localStorage.setItem("theme", theme);
    }
    const handleClick = () => {
      theme = (theme === "light" ? "dark" : "light");    
      console.log('classlist',document.documentElement.classList);    
    }; 

  </script>

<div class="w-42 h-24 border-1.5 border-lime-500 border-solid flex items-center justify-between p-2 relative cursor-pointer">
    <button class="text-xs" on:click={handleClick}>🌙</button>
    <button class="text-xs" on:click={handleClick}>🔆</button>
    <div
      class="w-16 h-16 bg-lime-500 rounded-full"
      class={theme === 'dark' ? "left" : theme === 'light' ? "right" : "2px"}
    />
</div>