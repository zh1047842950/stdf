<script>
	export let theme = false;
	export let inverse = false;
	export let size = 'w-8 h-8';
	export let customColor = [];
	export let speed = 1;

	const colorClass = () => {
		if (inverse) {
			return theme ? ' bg-dark dark:bg-primary' : ' bg-white dark:bg-black';
		} else {
			return theme ? ' bg-primary dark:bg-dark' : ' bg-black dark:bg-white';
		}
	};
</script>

<div class="{size} m-auto relative">
	{#each [0, 0.4, 0.8] as item, i}
		<div
			class="dot absolute top-0 left-0 flex items-center w-full h-full"
			style="animation-duration: {2.5 / speed}s;transform: translateX({32 * item}px);animation-delay: {2.5 / speed / (-1.5 * i)}s"
		>
			<div class="rounded-full w-2 h-2{colorClass()}" style="background-color: {customColor[0]};"></div>
		</div>
	{/each}
</div>

<style>
	.dot {
		animation: leapFrog ease infinite;
	}

	@keyframes leapFrog {
		0% {
			transform: translateX(0) rotate(0deg);
		}

		33.333% {
			transform: translateX(0) rotate(180deg);
		}

		66.666% {
			transform: translateX(calc(32px * -0.38)) rotate(180deg);
		}

		99.999% {
			transform: translateX(calc(32px * -0.78)) rotate(180deg);
		}

		100% {
			transform: translateX(0) rotate(0deg);
		}
	}
</style>
