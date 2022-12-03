<script lang="ts">
	import Compass from '../Compass.svelte';
	export let pageCount: number;
	$: active = pageCount === 1 ? true : false;
</script>

<div class="slide-content">
	<div class="content-container">
		<div class="compass-container">
			<Compass page={2} />
		</div>
		<div class="inner-wrapper">
			<div class="context {active ? 'active-slide' : 'inactive-slide'}">
				<h2 class="title">Story</h2>
				<p class="text">
					In a war-torn world, with the Wild Hunt on your back, you'll take on your most important
					contract -- to track down the child of prophecy, a key and a weapon which can save or
					destroy all.
				</p>
				<p />
			</div>
			<div class="tiles {active ? 'active-slide' : 'inactive-slide'}">
				<div class="tile">
					<img
						src="https://cdn-s-thewitcher.cdprojektred.com/witcher3/tiles/story-child-1.jpg"
						alt="Child Of Prophecy"
					/>
					<h3>Child Of Prophecy</h3>
				</div>
				<div class="tile">
					<img
						src="https://cdn-s-thewitcher.cdprojektred.com/witcher3/tiles/story-romance-1.jpg"
						alt="Romance"
					/>
					<h3>Romance</h3>
				</div>
				<div class="tile">
					<img
						src="https://cdn-s-thewitcher.cdprojektred.com/witcher3/tiles/story-plague-1.jpg"
						alt="Plague Of The Wild Hunt"
					/>
					<h3>Plague Of The Wild Hunt</h3>
				</div>
				<div class="tile">
					<img
						src="https://cdn-s-thewitcher.cdprojektred.com/witcher3/tiles/story-choice-1.jpg"
						alt="Choice And Consequence"
					/>
					<h3>Choice And Consequence</h3>
				</div>
			</div>
		</div>
	</div>
</div>

<style lang="scss">
	.inactive-slide {
		opacity: 0 !important;
		transform: translate3d(-200px, 0px, 0px) !important;
	}
	.compass-container {
		z-index: 2;
	}
	.content-container {
		height: 100vw;
		background-image: url('https://www.thewitcher.com/build/images/bg-story-81ca63b7..jpg');
		height: 100vh;
		position: relative;
		background-repeat: no-repeat;
		background-size: cover;
		background-position: 50%;
		.inner-wrapper {
			position: absolute;
			max-width: 800px;
			width: 41.6666666667vw;
			left: 140px;
			top: calc(50% + 56px);
			transform: translateY(-50%);
			.context {
				transition-duration: 550ms;
				transition-delay: 0.15s;
				h2 {
					opacity: inherit;
					font-weight: 700;
					font-size: 48px;
					line-height: 56px;
					margin: 0 0 17px;
					color: #fff;
					text-shadow: 0 2px 24px rgba(0, 0, 0, 0.6);
				}
				p {
					opacity: inherit;
					transition-timing-function: inherit;
					font-weight: 200;
					font-size: 16px;
					line-height: 28px;
					margin: 0;
					color: rgb(255, 255, 255);
					text-shadow: 0 2px 24px rgba(0, 0, 0, 0.6);
				}
			}
			.tiles {
				display: grid;
				grid-template: repeat(2, 1fr) / repeat(2, 1fr);
				gap: 40px;
				margin-top: 32px;
				transition-duration: 550ms;
				transition-delay: 0.25s;
				transform: translate3d(0px, 0px, 0px);
				.tile {
					position: relative;
					width: 100%;
					filter: drop-shadow(0 20px 32px rgba(0, 0, 0, 0.5));
					display: flex;
					align-items: flex-end;
					text-align: center;
					justify-content: center;
					cursor: pointer;
					aspect-ratio: 380/212;
					img {
						opacity: inherit;
						position: absolute;
						object-fit: cover;
						border-style: none;
						left: 0;
						top: 0;
						width: 100%;
						height: 100%;
						text-align: center;
						cursor: pointer;
					}
					h3 {
						opacity: inherit;
						position: relative;
						font-weight: 700;
						font-size: 27px;
						line-height: 34px;
						color: #fff;
						text-shadow: 0 2px 24px rgba(0, 0, 0, 0.6);
						margin: 0;
						padding: 26px;
						z-index: 5;
					}
				}
				.tile::after {
					opacity: inherit;
					content: '';
					box-sizing: border-box;
					position: absolute;
					left: 4px;
					right: 4px;
					top: 4px;
					bottom: 4px;
					border: 1px solid hsla(0, 0%, 100%, 0.2);
					z-index: 2;
					pointer-events: none;
				}
				.tile::before {
					opacity: inherit;
					content: '';
					position: absolute;
					height: 95px;
					left: 0;
					right: 0;
					bottom: 0;
					background: linear-gradient(180deg, transparent, #000 69.27%);
					opacity: 0.6;
					z-index: 1;
				}
			}
		}
	}
</style>
