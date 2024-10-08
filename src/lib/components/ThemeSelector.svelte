<script lang="ts">
  import { onMount } from 'svelte';
	import { writable } from 'svelte/store';
  import DropdownMenu from '$lib/components/DropdownMenu.svelte';

  // If you want to use the theme variable in other components, you can move it to a dedicated ts/js file and import it here instead
  let theme = writable<string>("system");
  
  // Define your themes and their names.
  const THEMES = [
      { value: 'system', label: 'Automatic' },
      { value: 'light', label: 'Light' },
      { value: 'dark', label: 'Dark' },
      { value: 'warm', label: 'Warm' },
  ];

  onMount(() => {
    // Prevents the code from running on the server
    if (typeof window == 'undefined') return;
    
    let storedTheme = localStorage.getItem('theme');
    
    // Get the user's system theme preference
    let systemTheme = window.matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light'; 
    
    if (storedTheme && THEMES.some(themeOption => themeOption.value === storedTheme)) {
      theme.set(storedTheme);
    } 
    else {
      theme.set('system');
      applyTheme(systemTheme);
    }

    // Update the automatic theme when the system theme changes if the theme is set to automatic
    window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', e => {
      systemTheme = e.matches ? 'dark' : 'light';
      if (storedTheme === 'system') {
        applyTheme(systemTheme);
      }
    });

    theme.subscribe(value => {
      if (value === 'system') {
        applyTheme(systemTheme);
      } 
      else {
        applyTheme(value);
      }

      localStorage.setItem('theme', value);
      storedTheme = value;
    });
  });

  function applyTheme(theme: string) {
    document.documentElement.className = "";
    if(theme === 'system') return;
   
    // Add the theme class (e.g dark-theme) to the document element to apply the theme
    document.documentElement.classList.add(`${theme}-theme`);
  }
  
</script>
  
<DropdownMenu>
  <svg slot="icon" width="37" height="37" viewBox="0 0 37 37" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M29 18.5C29 24.299 24.299 29 18.5 29C12.701 29 8 24.299 8 18.5C8 12.701 12.701 8 18.5 8C24.299 8 29 12.701 29 18.5Z" stroke="currentColor" stroke-width="2"/>
    <path d="M9 28L6.17157 30.8284" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
    <path d="M1 18.5H5" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
    <path d="M9 9L6.17157 6.17157" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
    <path d="M18.5 5L18.5 1" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
    <path d="M28 9L30.8284 6.17157" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
    <path d="M32 18.5H36" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
    <path d="M28 28L30.8284 30.8284" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
    <path d="M18.5 36L18.5 32" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
    <circle cx="14.5" cy="18.5" r="6.5" stroke="currentColor" stroke-width="2"/>
    <line x1="8.03459" y1="22.0512" x2="17.227" y2="12.8588" stroke="currentColor" stroke-width="2"/>
    <line x1="11.0346" y1="25.0512" x2="20.227" y2="15.8588" stroke="currentColor" stroke-width="2"/>
  </svg>  
  
  <div slot="dropdown">
    {#each THEMES as themeOption}
      <button 
        class="theme-button" 
        class:selected={$theme === themeOption.value}
        on:click={() => $theme = themeOption.value}
      >
        <svg width="24px" height="24px" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <circle cx="12" cy="12" r="7" fill="{$theme === themeOption.value ? 'var(--primary-60)' : 'transparent'}"/>
        </svg>
        <span>{themeOption.label}</span>
      </button>
    {/each}
  </div>
</DropdownMenu>
  
<style>
  :global(svg) {
    color: var(--neutral-70);
  }

  .theme-button.selected {
    font-weight: bold;
  }

  button {
    margin: 0;
    padding: 0;
    border: none;
    border-radius: 4px;
    background-color: transparent;
    color: inherit;
    cursor: pointer;
  }
</style>
  