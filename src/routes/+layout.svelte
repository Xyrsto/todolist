<script>
    import "../app.css";
</script>
  
<slot />

<style lang="postcss">
    :global(body) {
      @apply bg-gradient-to-r from-cyan-500 to-blue-500;
    }
  </style>