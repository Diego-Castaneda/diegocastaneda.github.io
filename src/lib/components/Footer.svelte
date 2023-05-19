<script>
	import Socials from "./Socials.svelte";
</script>
<footer>
    <div>
        <a href="/"><h1>Diego Castaneda</h1></a>
    </div>
    <Socials />
    <h6> © 2023 Diego Castaneda. All Rights Reserved. </h6>
</footer>

<style>
    footer {
        background-color: var(--color-bg-1);
        display: flex;
        flex-direction: column;
        align-items: center;
        padding-top: 2rem;
        gap: 1.5rem;
    }
    
    h6 {
        font-weight: 200;
    }
</style>