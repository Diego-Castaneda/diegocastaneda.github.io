<script>
	import { page } from '$app/stores';
	import logo from '$lib/images/svelte-logo.svg';
	import github from '$lib/images/github.svg';
	import ThemeToggle from './ThemeToggle.svelte';
</script>

<header>
	<div class="container flex-row">
		<div class="logo">
			<a href="/"><h1>Diego Castaneda</h1></a>
		</div>
		<nav>
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
	</div>	
</header>

<style>
	header {
		/* display: flex;
		justify-content: space-between; */
		background-color: var(--color-bg-1);
	}

	.page-links {
		margin-right: auto;
	}

	.flex-row {
		display: flex;
		justify-content: flex-start;
		align-items: center;
	}

	.logo {
		display: flex;
		justify-content: start;
		min-width: 320px;
		padding: 0;
		margin-right: 2rem;
	}

	.links {
		display: flex;
		align-items: center;
	}
	/* .corner a {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 100%;
	} */

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
</style>
