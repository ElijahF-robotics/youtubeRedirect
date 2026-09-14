<script>
  import { page } from '$app/state';
  import { dev } from '$app/environment';
  import { onMount } from 'svelte';

  let from = $derived(
      page.url.searchParams.get('from') ?? (dev ? 'https://example.com/test-origin' : null)
  );
  let isActive = $state(false)

  function goBack(target) {
    const url = new URL(target);
    url.searchParams.set('snooze', '10');
    window.location.href = url.toString();
  }

  function makeActive() {
    isActive = true;
  }

  onMount(() => {
    if (from && !dev) {
      setTimeout(makeActive, 10000)
    } else {
      isActive = true;
    }
  });
</script>

<div class="flex flex-col items-center justify-center bg-white p-4 rounded-lg max-w-1/3">
    {#if from}
      <p class="text-2xl">You've been Redirected!</p>
    {/if}

    <h1 class="my-10">Due to some force of nature you've been put on this page. If necessary the button below
        will soon activate. At that point you can travel back. But, ask yourself, do you really
        want to go back? Or are you going back just because it's normal. Or it's habitual?
        What would happen if you took the time to think here for a minute? Going back is always
        an option, but it's never mandatory.</h1>

    {#if from }
      <p class="text-sm text-gray-400 mb-4">Need to go back? Click the button below to return to <br> {from}</p>
      <button
        onclick={() => goBack(from)}
        class="p-2 rounded-lg {isActive ? 'bg-blue-100 hover:scale-105 hover:bg-blue-200 cursor-pointer active:scale-95 active:bg-blue-300' : 'bg-gray-200'}">
        Go Back
      </button>
    {/if}
</div>
