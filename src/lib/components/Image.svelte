<script>
	import { onMount } from 'svelte'
	export let src;
    export let alt;

	let loaded = false;
	let failed = false;
	let loading = false;

	onMount(() => {
        const img = new Image();
        img.src = src;
        loading = true;

        img.onload = () => {
                loading = false;
                loaded = true;
        };
        img.onerror = () => {
                loading = false;
                failed = true;
        };
	})
</script>

{#if loaded}
    <img {src} {alt}/>
{:else if failed}
	<img src="https://icon-library.com/images/not-found-icon/not-found-icon-20.jpg" alt="Not Found" />
{:else if loading}
	<img src="https://c.tenor.com/On7kvXhzml4AAAAi/loading-gif.gif" alt="Loading..." />
{/if}

<style>
    img {
        width: 100%;
        height: 100%;
    }
</style>
