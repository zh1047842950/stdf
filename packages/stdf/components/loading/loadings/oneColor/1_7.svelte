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

<div class={`${size} m-auto flex items-center`}>
	<div
		class={`flex-1${colorClass()} rounded-full w-1/2 h-1/2 loading1`}
		style="background: {customColor[0]};animation-duration: {1 / speed}s;-webkit-animation-duration: {1 / speed}s;"
	/>
	<div
		class={`flex-1${colorClass()} rounded-full w-1/2 h-1/2 loading2`}
		style="background: {customColor[0]};animation-duration: {1 / speed}s;-webkit-animation-duration: {1 / speed}s;"
	/>
</div>

<style>
	.loading1 {
		animation: loading infinite 1s -0.4s cubic-bezier(0.2, 0.68, 0.18, 1.08);
	}

	.loading2 {
		animation: loading infinite 1s cubic-bezier(0.2, 0.68, 0.18, 1.08);
	}

	@keyframes loading {
		0% {
			transform: scale(1);
			opacity: 1;
		}
		50% {
			transform: scale(0.1);
			opacity: 0.6;
		}
		100% {
			transform: scale(1);
			opacity: 1;
		}
	}
</style>
