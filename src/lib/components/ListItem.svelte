<script>
  export let id = ""; 
  export let title = "Title";

  import { createEventDispatcher } from 'svelte';
  import { fade } from 'svelte/transition';

  const dispatch = createEventDispatcher();
  let isVisible = true;

  function handleDelete() {
      isVisible = false; 
      setTimeout(() => {
          dispatch('delete', { id }); 
      }, 250); 
  }
</script>

{#if isVisible}
  <div
      class="outline outline-offset-2 outline-pink-400 hover:outline-pink-500 bg-cyan-500 p-4 rounded-lg w-5/6 h-20 shadow-lg flex justify-between items-center"
      transition:fade
      on:outroend={() => isVisible = false} 
      style="opacity: 1;"
  >
      <h3 class="text-white text-xl">{title}</h3>
      <button
          class="rounded bg-cyan-600 hover:bg-cyan-700 text-white py-2 px-4"
          on:click={handleDelete}>Done</button>
  </div>
{/if}


