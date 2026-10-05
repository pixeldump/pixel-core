<script lang="ts">
	import { onMount } from 'svelte';

	const links = [
		{ href: '#hero', label: 'Home' },
		{ href: '#about', label: 'About' },
		{ href: '#projects', label: 'Projects' },
		{ href: 'https://pixeldump.github.io/pixel-dump', label: 'Blog', target: '_blank' },
		{ href: '#contact', label: 'Contact' }
	];

	let open = $state(false);
	let dark = $state(false);
	let locked = $state(false);

	onMount(() => {
		const stored = localStorage.getItem('theme');
		if (stored) {
			locked = true;
			dark = stored === 'dark';
		} else {
			dark = window.matchMedia('(prefers-color-scheme: dark)').matches;
		}
		document.documentElement.classList.toggle('dark', dark);

		const mq = window.matchMedia('(prefers-color-scheme: dark)');
		const onChange = (e: MediaQueryListEvent) => {
			if (locked) return;
			dark = e.matches;
			document.documentElement.classList.toggle('dark', dark);
		};
		mq.addEventListener('change', onChange);
		return () => mq.removeEventListener('change', onChange);
	});

	function toggleTheme() {
		dark = !dark;
		locked = true;
		localStorage.setItem('theme', dark ? 'dark' : 'light');
		document.documentElement.classList.toggle('dark', dark);
	}
</script>

<header class="sticky top-0 z-50 border-b border-line bg-bg">
	<nav class="mx-auto flex h-16 max-w-6xl items-center justify-between px-6" aria-label="Primary">
		<a href="#hero" rel="external" class="text-xl font-bold tracking-tight text-fg">
			<span class="text-accent">&gt;_</span> PixelCore
		</a>

		<div class="hidden items-center gap-8 md:flex">
			{#each links as link (link.href)}
				<a
					href={link.href}
					rel="external"
					target={link.target ?? '_self'}
					class="text-sm tracking-wider text-muted uppercase transition-colors hover:text-accent"
				>
					{link.label}
				</a>
			{/each}
		</div>

		<div class="flex items-center gap-3">
			<button
				type="button"
				class="flex h-9 w-9 items-center justify-center rounded border border-line text-muted transition-colors hover:border-accent hover:text-accent"
				aria-label="Toggle theme"
				onclick={toggleTheme}
			>
				{#if dark}
					<svg
						xmlns="http://www.w3.org/2000/svg"
						class="h-5 w-5"
						fill="none"
						viewBox="0 0 24 24"
						stroke="currentColor"
						stroke-width="2"
					>
						<circle cx="12" cy="12" r="4" />
						<path
							stroke-linecap="round"
							d="M12 2v2m0 16v2M4.93 4.93l1.41 1.41m11.32 11.32 1.41 1.41M2 12h2m16 0h2M6.34 17.66l-1.41 1.41M19.07 4.93l-1.41 1.41"
						/>
					</svg>
				{:else}
					<svg
						xmlns="http://www.w3.org/2000/svg"
						class="h-5 w-5"
						fill="currentColor"
						viewBox="0 0 24 24"
					>
						<path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z" />
					</svg>
				{/if}
			</button>

			<button
				type="button"
				class="flex h-9 w-9 items-center justify-center rounded border border-line text-muted transition-colors hover:border-accent hover:text-accent md:hidden"
				aria-label="Toggle menu"
				aria-expanded={open}
				onclick={() => (open = !open)}
			>
				{#if open}
					<svg
						xmlns="http://www.w3.org/2000/svg"
						class="h-5 w-5"
						fill="none"
						viewBox="0 0 24 24"
						stroke="currentColor"
						stroke-width="2"
					>
						<path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
					</svg>
				{:else}
					<svg
						xmlns="http://www.w3.org/2000/svg"
						class="h-5 w-5"
						fill="none"
						viewBox="0 0 24 24"
						stroke="currentColor"
						stroke-width="2"
					>
						<path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
					</svg>
				{/if}
			</button>
		</div>
	</nav>

	{#if open}
		<div class="border-t border-line bg-panel px-6 py-4 md:hidden">
			{#each links as link (link.href)}
				<a
					href={link.href}
					rel="external"
					class="block py-2.5 text-xs tracking-wider text-muted uppercase transition-colors hover:text-accent"
					onclick={() => (open = false)}
				>
					{link.label}
				</a>
			{/each}
		</div>
	{/if}
</header>
