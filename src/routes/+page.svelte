<script>
  import { page } from '$app/state';

  let from = $derived(page.url.searchParams.get('from'));
</script>

{#if from}
  <p>You were redirected from: {from}</p>
{/if}

<h1>You've Been Redirected, Congrats!</h1>
<p>Here's why I don't like youtube:</p>

<!-- {#if from} -->
    <p>Need to go back? Click the button below to return to {from}</p>
    <button onclick={() => goto(from + "?snooze=10")} class="bg-blue-100 hover:bg-blue-200 cursor-pointer active:scale-95 active:bg-blue-300 p-2 rounded-lg hover:scale-105">Go Back</button>
<!-- {/if} -->
