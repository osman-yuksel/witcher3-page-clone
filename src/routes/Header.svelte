<script lang="ts">
	let dropdownActive = false;
	$: dropdownClass = dropdownActive ? 'dropdown-menu-active' : '';

	function ToggleDropdown() {
		dropdownActive = !dropdownActive;
	}
</script>

<header class="navbar-black">
	<nav>
		<ul>
			<li
				class="dropdown-container {dropdownClass}"
				on:click={ToggleDropdown}
				on:keypress={ToggleDropdown}
			>
				<span>GAMES</span>
				<ul class="dropdown-menu {dropdownClass}">
					<li>
						<a href="https://www.thewitcher.com/monster-slayer">THE WITCHER: MONSTER SLAYER</a>
					</li>
					<li>
						<a href="https://thewitcher.com/thronebreaker-witchertales"
							>THRONEBREAKER: THE WITCHER TALES</a
						>
					</li>
					<li><a href="https://playgwent.com/">GWENT®: The Witcher Card Game</a></li>
					<li><a href="http://thewitcher.com/witcher3">THE WITCHER 3: WILD HUNT</a></li>
					<li><a href="http://thewitcher.com/witcher2">THE WITCHER 2: ASSASSINS OF KINGS</a></li>
					<li><a href="http://thewitcher.com/witcher1">THE WITCHER: ENHANCED EDITION</a></li>
					<li><a href="https://thewitcher.com/adventuregame/">THE WITCHER ADVENTURE GAME</a></li>
				</ul>
			</li>
			<li>
				<a href="#news">NEWS</a>
			</li>
			<li>
				<a href="#community">COMMUNITY</a>
			</li>
			<li>
				<a href="#media">MEDIA</a>
			</li>
			<li>
				<a href="#home">
					<button> BUY NOW </button>
				</a>
			</li>
		</ul>
	</nav>
</header>

<style lang="scss">
	header {
		font-family: Assistant;
		font-weight: bold;
		letter-spacing: 0.1rem;
		position: fixed;
		right: 4rem;
		font-size: 18px;
		z-index: 100;
		transition: color 0.15s;
		user-select: none;
	}

	.dropdown-menu {
		text-align: start;
		list-style: none;
		padding: 0;
		margin: 0;
		flex-direction: column;
		align-items: flex-start;
		padding-top: 16px;
		padding-right: 32px;
		padding-bottom: 16px;
		padding-left: 32px;
		width: 100vw;
		max-width: 430px;
		background: hsla(0, 0%, 100%, 0.7);
		border: 1px solid #91a198;
		border-top-color: rgb(145, 161, 152);
		border-top-style: solid;
		border-top-width: 1px;
		border-right-color: rgb(145, 161, 152);
		border-right-style: solid;
		border-right-width: 1px;
		border-bottom-color: rgb(145, 161, 152);
		border-bottom-style: solid;
		border-bottom-width: 1px;
		border-left-color: rgb(145, 161, 152);
		border-left-style: solid;
		border-left-width: 1px;
		border-image-outset: 0;
		border-image-repeat: stretch;
		border-image-slice: 100%;
		border-image-source: none;
		border-image-width: 1;
		box-sizing: border-box;
		box-shadow: 0 20px 32px rgba(63, 101, 97, 0.3);
		position: absolute;
		transform: translateY(-10px);
		top: 30px;
		left: -32px;
		display: flex;
		opacity: 0;
		pointer-events: none;
		transition: opacity 0.2s, transform 0.2s;
		font-weight: normal;
		letter-spacing: -1px;
		@supports not ((backdrop-filter: blur(32px)) and (-webkit-backdrop-filter: blur(32px))) {
			background: hsla(0, 0%, 100%, 0.8);
		}
		@supports (backdrop-filter: blur(32px)) {
			backdrop-filter: blur(32px);
		}
		li {
			margin-top: 12px;
			margin-bottom: 12px;
		}
	}

	.dropdown-container {
		position: relative;

		span{
			margin-right: 2px;
		}
	}

	.dropdown-container::before {
		content: '';
		display: block;
		position: absolute;
		top: calc(50% - 2px);
		right: 0;
		width: 0;
		height: 0;
		transition: border 0.2s;
		border: 4px solid transparent;
		border-top-color: transparent;
		border-top-style: solid;
		border-top-width: 4px;
		border-bottom-color: transparent;
		border-bottom-style: solid;
		border-bottom-width: 4px;
		border-bottom: 0;
		border-top: 4px solid #000;
		pointer-events: none;
	}

	.dropdown-menu-active {
		ul {
			opacity: 1;
			pointer-events: all;
			top: 30px;
			transform: translateY(0);
		}

		span {
			top: 2px;
			border-bottom: 2px solid #000;
			height: 21px;
		}
	}

	.dropdown-menu-active::before {
		border-top: 0;
		border-bottom: 4px solid #000;
	}

	.navbar-black {
		color: black;
		span {
			transition: inherit;
			&:hover {
				color: #e60000;
				cursor: pointer;
			}
			padding-inline-end: 12px;
		}
		a {
			&:hover {
				color: #e60000;
			}
		}
	}

	nav {
		display: flex;
		flex-direction: row;
		justify-content: center;
		transition: inherit;
	}

	ul {
		display: flex;
		flex-direction: row;
		align-items: center;
		transition: inherit;
		li {
			margin-left: 20px;
			margin-right: 20px;
			list-style-type: none;
			display: flex;
			transition: inherit;
			a {
				color: inherit;
				transition: inherit;
				text-decoration: none;

				button {
					color: rgb(230, 0, 0);
					font-size: 18px;
					min-width: 108px;
					height: 32px;
					margin-left: 14px;
					margin-right: 14px;
					background-size: contain;
					background-image: url('https://www.thewitcher.com/build/images/middle-33abf525..png');
					background-repeat: repeat-x;
					display: flex;
					align-items: center;
					justify-content: center;
					text-align: center;
					white-space: nowrap;
					cursor: pointer;
					border: none;
					position: relative;
					font-family: Assistant;
					font-weight: bold;
					box-shadow: 0 12px 24px rgba(63, 101, 97, 0.3);
				}

				button::before {
					content: '';
					display: block;
					position: absolute;
					height: 32px;
					width: 15px;
					background-size: contain;
					background-image: url('https://www.thewitcher.com/build/images/left-bc2cd3e3..png');
					background-repeat: no-repeat;
					left: -14px;
				}

				button::after {
					content: '';
					display: block;
					position: absolute;
					height: 32px;
					width: 15px;
					background-size: contain;
					background-image: url('https://www.thewitcher.com/build/images/right-26e93501..png');
					background-repeat: no-repeat;
					right: -14px;
				}
			}
		}
	}
</style>
