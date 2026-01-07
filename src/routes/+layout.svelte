<script lang="ts">
import type { Snippet } from 'svelte';
import '../main.css';

const { children }: { children: Snippet } = $props();

// 生成随机星星位置
const stars = Array.from({ length: 100 }, (_, i) => {
	const size = Math.random();
	let sizeClass = 'star-sm';
	let duration = 2 + Math.random() * 3;
	let delay = Math.random() * 5;

	if (size > 0.7) {
		sizeClass = 'star-lg';
		duration = 3 + Math.random() * 4;
	} else if (size > 0.4) {
		sizeClass = 'star-md';
		duration = 2.5 + Math.random() * 3.5;
	}

	return {
		id: i,
		left: Math.random() * 100,
		top: Math.random() * 100,
		sizeClass,
		duration,
		delay
	};
});
</script>

<svelte:head>
	<style>
		/* 确保背景显示 */
		:global(body) {
			background: transparent !important;
		}
	</style>
</svelte:head>

<!-- 星空背景层 -->
<div class="starry-background">
	{#each stars as star (star.id)}
		<div
			class="star {star.sizeClass}"
			style="left: {star.left}%; top: {star.top}%; --duration: {star.duration}s; --delay: {star.delay}s;"
			aria-hidden="true"
		></div>
	{/each}
</div>

<!-- 玻璃板内容容器 - 铺满整个窗口，添加明显边框 -->
<div
	class="fixed inset-0 z-50 m-0 overflow-hidden rounded-xl border-2 border-white/20 bg-white/[0.02] backdrop-blur-md shadow-2xl dark:border-white/20 dark:bg-white/[0.02]"
>
	{@render children()}
</div>
