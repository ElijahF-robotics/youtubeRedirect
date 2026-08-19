<script>
  let from = new URLSearchParams(window.location.search).get('from');
</script>

{#if from}
  <p>You were redirected from: <a href={from}>{from}</a></p>
{/if}

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the documentation</p>
