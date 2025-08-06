<!-- src/routes/+page.svelte
<h2>🏠 Welcome to Haritha’s App</h2>
<p>Select where to go:</p>

<ul>
  <li><a href="/login">Login</a></li>
</ul> -->

<script>
    import { onMount } from 'svelte';
    import { goto } from '$app/navigation';
  
    onMount(() => {
      goto('/login');
    
    });
</script>
  
<p>Redirecting to login...</p>
  