<script lang="ts">
	// @ts-ignore
	import Header from './Header.svelte';
	import Witcher3Logo from './Witcher3Logo.svelte';
	import { onMount } from 'svelte';

	//Slider Pages
	import SliderPage1 from './sliders/SliderPage1.svelte';
	import SliderPage2 from './sliders/SliderPage2.svelte';

	//Slider logic
	let pageCount = 0;
	let isScroolable = true;
	let viewport_height = 0;

	import { tweened } from 'svelte/motion';
	import { cubicOut } from 'svelte/easing';

	const scrollableYPosition = tweened(0, {
		duration: 400,
		easing: cubicOut
	});

	onMount(() => {
		viewport_height = window.innerHeight;
	});

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

	function resizeListener() {
		viewport_height = window.innerHeight;
		scrollableYPosition.set(viewport_height * pageCount);
	}
</script>

<svelte:window on:resize={resizeListener} />

<Header {pageCount} />
<Witcher3Logo {pageCount} />

<main
	class="container"
	on:wheel={scrollHandler}
	style="--scrollableYPosition: {$scrollableYPosition}"
>
	<div class="slider-page-container">
		<span>{$scrollableYPosition}</span>
		<SliderPage1 />
	</div>
	<div class="slider-page-container">
		<span>{$scrollableYPosition}</span>
		<SliderPage2 {pageCount}/>
	</div>
	<div class="slider-page-container c"><span>{$scrollableYPosition}</span></div>
	<div class="slider-page-container d"><span>{$scrollableYPosition}</span></div>
	<div class="slider-page-container e"><span>{$scrollableYPosition}</span></div>
	<div class="slider-page-container f"><span>{$scrollableYPosition}</span></div>
	<div class="slider-page-container g"><span>{$scrollableYPosition}</span></div>
</main>

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

	.slider-page-container {
		margin: 0;
		height: 100vh;
		width: 100%;

		span {
			position: absolute;
			z-index: 10;
		}
	}

	.c,
	.e,
	.g {
		background-color: red;
	}
</style>
