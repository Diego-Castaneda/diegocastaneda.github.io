<script>
    import GithubIcon from '../icons/github.svelte';
    import LinkedinIcon from '../icons/linkedin.svelte';
</script>

<div class="socials">
    <a 
        href="https://github.com/Diego-Castaneda" 
        title="See my Github profile"
        target="_blank"
    >
        <GithubIcon />
    </a>
    <a 
        href="https://www.linkedin.com/in/diego-castaneda-lego/"
        title="See my on LinkedIn"
        target="_blank"
    >
        <LinkedinIcon />
    </a>
</div>

<style>
    .socials {
        display: flex;
        gap: 20px;
        fill: var(--color-text);
    }

    .socials a {
        width: 32px;
    }

    .socials a:hover {
        filter: drop-shadow(0px 0px 3px var(--color-primary));
    }
</style>