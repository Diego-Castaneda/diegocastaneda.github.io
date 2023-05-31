<script>
    import { page } from '$app/stores';
    import ThemeToggle from './ThemeToggle.svelte';
    import MenuIcon from '$lib/icons/menu-outline.svelte';
</script>
<div class="menu-icon mobile-only-nav">
	<MenuIcon></MenuIcon>
</div>

<nav class="desktop-nav">
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
<style>
    .menu-icon {
        width: 50px;
        height: 50px;
        background: none;
        border: none;
        fill: none;
        margin-left: auto;
    }
    
    .mobile-only-nav {
		margin-left: auto;
	}

	.desktop-nav {
		display: none;
	}

	.links {
		margin-left: auto;
		display: flex;
		align-items: center;
	}

	nav {
		display: flex;
		--background: rgba(255, 255, 255, 0.7);
		width: 100%;
	}

	ul {
		position: relative;
		padding: 0;
		margin: 0;
		height: 3em;
		display: flex;
		justify-content: start;
		align-items: center;
		list-style: none;
		background-size: contain;
	}

	li[aria-current='page']::before {
		--size: 6px;
		content: '';
		width: 0;
		height: 0;
		position: absolute;
		top: 0;
		left: calc(50% - var(--size));
		border: var(--size) solid transparent;
		border-top: var(--size) solid var(--color-theme-1);
	}

	nav a {
		display: flex;
		height: 100%;
		align-items: center;
		padding: 0 0.5rem;
		color: var(--color-text);
		font-weight: 700;
		font-size: 0.8rem;
		text-transform: uppercase;
		letter-spacing: 0.1em;
		text-decoration: none;
		transition: color 0.2s linear;
	}

	a:hover {
		color: var(--color-theme-1);
	}

	@media (min-width: 615px) {
		.mobile-only-nav {
			display: none;
		}
		
		.desktop-nav {
			display: contents;
		}	
	}
</style>