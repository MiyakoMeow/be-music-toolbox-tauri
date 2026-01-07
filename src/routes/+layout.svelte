<script lang="ts">
import type { Snippet } from 'svelte';
import '../main.css';
import StarryBackground from '$lib/components/StarryBackground.svelte';

const { children }: { children: Snippet } = $props();
</script>

<div class="layout-container">
  <StarryBackground />
  <div class="content-layer">
    {@render children()}
  </div>
</div>

<style>
  .layout-container {
    position: relative;
    min-height: 100vh;
    width: 100%;
  }
</style>
