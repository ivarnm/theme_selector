<script>
  import '../styles/global.css';
  import ThemeSelector from '$lib/components/ThemeSelector.svelte';
</script>

<div>
  <header>
    <ThemeSelector />
  </header>
  <main>
    <slot />
  </main>
</div>

<style>
  header {
    display: flex;
    justify-content: flex-end;
  }

  main {
    margin: 50px 0;
  }
</style>
