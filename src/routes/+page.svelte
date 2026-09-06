<script>
  import { page } from '$app/state';

  let from = $derived(page.url.searchParams.get('from'));

  function goBack(target) {
    const url = new URL(target);
    url.searchParams.set('snooze', '10');
    window.location.href = url.toString();
  }
</script>

{#if from}
  <p>You were redirected from: {from}</p>
{/if}

<h1>You've Been Redirected, Congrats!</h1>

{#if from}
  <p>Need to go back? Click the button below to return to {from}</p>
  <button
    onclick={() => goBack(from)}
    class="bg-blue-100 hover:bg-blue-200 cursor-pointer active:scale-95 active:bg-blue-300 p-2 rounded-lg hover:scale-105">
    Go Back
  </button>
{/if}
