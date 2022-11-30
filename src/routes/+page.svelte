<script lang="ts">
	// @ts-ignore
	import Header from './Header.svelte';
	import { onMount } from 'svelte';

	let pageCount = 0;
	let isScroolable = true;
	let viewport_height = 0;

	import { tweened } from 'svelte/motion';
	import { cubicOut } from 'svelte/easing';

	const scrollableYPosition = tweened(0, {
		duration: 300,
		easing: cubicOut
	});

	onMount(() => {
		viewport_height = window.innerHeight;
	});

	function resizeListener() {
		viewport_height = window.innerHeight;
		scrollableYPosition.set(viewport_height * pageCount);
	}

	function scrollHandler(event: any) {
		if (isScroolable) {
			if (event.deltaY > 0) pageCount = pageCount === 6 ? 6 : ++pageCount;
			else pageCount = pageCount === 0 ? 0 : --pageCount;

			scrollableYPosition.set(viewport_height * pageCount);

			isScroolable = false;
			setTimeout(() => {
				isScroolable = true;
			}, 500);
		}
	}
</script>

<svelte:window on:resize={resizeListener} />

<Header />
<div
	class="container"
	on:wheel={scrollHandler}
	style="--scrollableYPosition: {$scrollableYPosition}"
>
	<div class="dummy a"><p>{$scrollableYPosition}</p></div>
	<div class="dummy b"><p>{$scrollableYPosition}</p></div>
	<div class="dummy c"><p>{$scrollableYPosition}</p></div>
	<div class="dummy d"><p>{$scrollableYPosition}</p></div>
	<div class="dummy e"><p>{$scrollableYPosition}</p></div>
	<div class="dummy f"><p>{$scrollableYPosition}</p></div>
	<div class="dummy g"><p>{$scrollableYPosition}</p></div>
</div>

<style lang="scss">
	:global(body) {
		margin: 0;
	}
	@media only screen and (min-width: 1000px) {
		:global(body) {
			overflow: hidden;
		}
	}
	.container {
		width: 100vw;
		position: relative;
		transform: translate3d(0px, calc(var(--scrollableYPosition) * -1px), 0px);
		z-index: 1;
		display: flex;
		flex-direction: column;
		transition-property: transform;
		box-sizing: content-box;
	}

	.dummy {
		margin: 0;
		height: 100vh;
		width: 100%;

		p {
			margin: 0;
		}
	}

	.a,
	.c,
	.e,
	.g {
		background-color: red;
	}
</style>
