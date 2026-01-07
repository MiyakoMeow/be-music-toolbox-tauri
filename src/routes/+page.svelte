<script lang="ts">
import { invoke } from '@tauri-apps/api/core';

let name = $state('');
let greetMsg = $state('');

async function greet(event: Event) {
  event.preventDefault();
  // Learn more about Tauri commands at https://tauri.app/develop/calling-rust/
  greetMsg = await invoke('greet', { name });
}
</script>

<main class="flex h-full flex-col items-center justify-center p-8 text-center">
  <h1 class="text-center text-2xl font-bold dark:text-white">Welcome to Tauri + Svelte</h1>

  <div class="flex justify-center">
    <a
      href="https://vite.dev"
      target="_blank"
      class="
        text-link hover:text-link-hover font-medium
        no-underline
        transition-transform
        hover:scale-110 dark:hover:text-[#24c8db]
      "
    >
      <img
        src="/vite.svg"
        class="
          h-24 p-6 transition-[0.75s]
          hover:drop-shadow-[0_0_2em_#747bff]
        "
        alt="Vite Logo"
      />
    </a>
    <a
      href="https://tauri.app"
      target="_blank"
      class="
        text-link hover:text-link-hover font-medium
        no-underline
        transition-transform
        hover:scale-110 dark:hover:text-[#24c8db]
      "
    >
      <img
        src="/tauri.svg"
        class="
          h-24 p-6 transition-[0.75s]
          hover:drop-shadow-[0_0_2em_#24c8db]
        "
        alt="Tauri Logo"
      />
    </a>
    <a
      href="https://svelte.dev"
      target="_blank"
      class="text-link hover:text-link-hover dark:hover:text-shadow-svelte font-medium no-underline transition-transform hover:scale-110"
    >
      <img
        src="/svelte.svg"
        class="
          h-24 p-6 transition-[0.75s]
          hover:drop-shadow-[0_0_2em_#ff3e00]
        "
        alt="SvelteKit Logo"
      />
    </a>
  </div>

  <p class="mb-6 text-sm opacity-90 dark:text-gray-300">
    Click on the Tauri, Vite, and SvelteKit logos to learn more.
  </p>

  <form class="flex justify-center gap-2" onsubmit={greet}>
    <input
      id="greet-input"
      placeholder="Enter a name..."
      bind:value={name}
      class="
        text-text-primary dark:bg-dark-bg-secondary rounded-lg border
        border-transparent bg-white/80 px-[1.2em] py-[0.6em]
        text-base font-medium
        shadow-[0_2px_2px_rgba(0,0,0,0.2)]
        backdrop-blur-sm transition-[border-color_0.25s]
        outline-none
        dark:text-white
      "
    />
    <button
      type="submit"
      class="
        text-text-primary hover:border-border-focus active:border-border-focus active:bg-bg-active
        dark:bg-dark-bg-secondary dark:active:bg-dark-bg-active cursor-pointer rounded-lg
        border border-transparent
        bg-white/80
        px-[1.2em]
        py-[0.6em] text-base
        font-medium shadow-[0_2px_2px_rgba(0,0,0,0.2)] backdrop-blur-sm
        transition-[border-color_0.25s]
        outline-none
        dark:text-white
      "
    >
      Greet
    </button>
  </form>

  {#if greetMsg}
    <p class="mt-4 rounded-lg bg-white/20 p-4 backdrop-blur-sm dark:bg-white/10">
      {greetMsg}
    </p>
  {/if}
</main>
