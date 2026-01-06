<script lang="ts">
import type { Snippet } from 'svelte';
import '../main.css';
import StarryBackground from '$lib/components/StarryBackground.svelte';

const { children }: { children: Snippet } = $props();
</script>

<StarryBackground />
<div class="content-layer">
  {@render children()}
</div>
