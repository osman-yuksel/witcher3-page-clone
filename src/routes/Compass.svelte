<script lang="ts">
	export let page: number;
</script>

<div class="compass slide-{page}-compass" style="--page: {page}">
	<img src="https://www.thewitcher.com/build/images/Compass-0c9152d4..svg" alt="Compass">
</div>

<style lang="scss">
	$size: 670px;
	.compass {
		pointer-events: none;
		position: absolute;
		top: 0;
		left: 0;
		width: $size;
		height: $size;
		overflow: hidden;
		transform: rotate(180deg);
		img{
			position: relative;
			width: 200%;
			height: 200%;
			rotate: (calc(180deg + var(--page) * 100deg));
		}
	}

	.slide-1-compass{
		mix-blend-mode: overlay;
		opacity: .3;
	}
	.slide-2-compass{
		mix-blend-mode: color-burn;
		opacity: 1;
	}
</style>
