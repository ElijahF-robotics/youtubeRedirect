<script>
  import { page } from '$app/state';

  let from = $derived(page.url.searchParams.get('from'));
</script>

{#if from}
  <p>You were redirected from: {from}</p>
{/if}

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the documentation</p>

{#if from}
    <p> To go back click this link: <a href={from}>{from + "?snooze=10"}</a></p>
{/if}
