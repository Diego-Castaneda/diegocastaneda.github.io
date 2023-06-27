<script>
    import { page } from '$app/stores';
	import { fly, fade } from 'svelte/transition';
    import ThemeToggle from './ThemeToggle.svelte';
    import MenuIcon from '$lib/icons/menu-outline.svelte';

	let innerWidth = 0;
	$: mobilePortalEnabled = innerWidth < 615;
	let mobilePortalOpen = false;
	$: backdropVisible = mobilePortalOpen;
	$: navbarVisible = mobilePortalOpen || !mobilePortalEnabled;

	let transitionParams = { x: -100, duration: 300 };
	$: if (innerWidth < 615) {
		// Add a delay to ensure that the "modal" navbar doesn't flash when transitioning to a mobile portal.
		setTimeout( () => transitionParams = { x: -100, duration: 300 }, 200 );
	}
	else {
		transitionParams = { x: 0, duration: 0 };
	}


</script>

<svelte:window bind:innerWidth/>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<div on:click="{() => mobilePortalOpen = !mobilePortalOpen}" class="menu-icon mobile-only-nav">
	<MenuIcon></MenuIcon>
</div>

{#if backdropVisible}
	<div class="backdrop" transition:fade="{{duration: 300}}"></div>
{/if}

{#if navbarVisible}
	<nav in:fly="{transitionParams}" out:fly="{transitionParams}">
		<ul class="page-links">
			<li><a href="#">Latest</a></li>
			<li><a href="#">Notes</a></li>
			<li aria-current={$page.url.pathname === '/home' ? 'page' : undefined}>
				<a href="/home">Homie</a>
			</li>
		</ul>

		<div class="links">
			<ThemeToggle />
		</div>
	</nav>
{/if}
<style>
    .menu-icon {
        width: 50px;
        height: 50px;
        background: none;
        border: none;
        fill: none;
        margin-left: auto;
		z-index: 10001;
    }
    
    .mobile-only-nav {
		margin-left: auto;
	}

	.links {
		margin-top: 6rem;
	}

	.backdrop {
		position: absolute;
		height: 100%;
		width: 100%;
		top: 0;
		left: 0;
		background: rgba(255, 255, 255, 0.7);
		backdrop-filter: blur(10px);	
	}

	nav {
		position: absolute;
		display: flex;
		flex-direction: column;
		align-items: start;
		top: 20%;
		left: 0;
		margin-left: 2rem;
	}

	ul {
		padding: 0;
		margin: 0;
		display: flex;
		flex-direction: column;
		justify-content: start;
		align-items: center;
		list-style: none;
		background-size: contain;
	}
	
	li {
		margin-top: 2rem;
	}

	nav a {
		display: flex;
		height: 100%;
		align-items: center;
		padding: 0 0.5rem;
		color: var(--color-text);
		font-weight: 700;
		text-transform: uppercase;
		letter-spacing: 0.1em;
		text-decoration: none;
		transition: color 0.2s linear;
		font-size: 2rem;
	}

	a:hover {
		color: var(--color-theme-1);
	}

	@media (min-width: 615px) {
		nav a {
			font-size: 1rem;
		}
		
		.mobile-only-nav {
			display: none;
		}
	
		nav {
			flex-direction: row;
			align-items: center;
			position: static;
		}

		ul {
			flex-direction: row;
		}

		li {
			margin-top: 0;
		}

		.links {
			margin-left: auto;
			margin-top: 0;
			display: flex;
			align-items: center;
		}
	}
</style>