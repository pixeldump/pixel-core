<script lang="ts">
	const channels = [
		{ label: 'Email', value: 'm.arkamfahry@gmail.com', href: 'mailto:m.arkamfahry@gmail.com' },
		{ label: 'GitHub', value: 'github.com/pixeldump', href: 'https://github.com/pixeldump' },
		{ label: 'Twitter / X', value: '@pixeldumpdev', href: 'https://x.com/pixeldumpdev' }
	];
</script>

<section id="contact" class="border-t border-line bg-panel py-20">
	<div class="mx-auto max-w-6xl px-6">
		<h2 class="text-sm text-muted">
			<span class="text-syn-orange">03</span> // transmit
		</h2>
		<p class="mt-4 max-w-2xl text-3xl font-semibold tracking-tight text-fg sm:text-4xl">
			Open a channel. Let's talk.
		</p>

		<div class="mt-10 max-w-3xl">
			{#each channels as channel (channel.href)}
				<a
					href={channel.href}
					rel="external"
					class="group flex items-baseline justify-between gap-4 border-b border-line-strong py-4 transition-colors hover:border-accent"
				>
					<span
						class="text-xs tracking-wider text-muted uppercase transition-colors group-hover:text-accent"
					>
						{channel.label}
					</span>
					<span class="text-sm text-fg transition-colors group-hover:text-accent">
						{channel.value}
					</span>
				</a>
			{/each}
		</div>
	</div>
</section>
