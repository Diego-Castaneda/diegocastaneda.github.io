<script>
	import { page } from '$app/stores';
	import Wave from '$lib/components/wave.svelte';
	import NavBar from '$lib/components/NavBar.svelte';

</script>

<header>
	<div class="top-height"></div>

	<div class="container flex-row">
		<div class="logo"><h1><a href="/">Diego Castaneda</a></h1></div>

		<NavBar></NavBar>
	</div>

	<div class="bottom-height"></div>
	<Wave />
</header>

<style>
	header {
		background-color: var(--color-bg-1);
		margin-right: 0;
	}

	.top-height {
		background-color: var(--color-bg-1);
		width: 100%;
		height: 50px;
		visibility: hidden;
	}

	.bottom-height {
		width: 100%;
		height: 200px;
	}

	.logo {
		display: flex;
		justify-content: start;
		margin-right: 1rem;
		min-width: 265px;
	}

	@media (min-width: 615px) {
		.top-height {
			visibility: visible;
		}
	}
</style>
