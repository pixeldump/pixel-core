<script lang="ts">
	const skills = [
		{ name: 'Thinking', className: 'text-syn-red' },
		{ name: 'Taste', className: 'text-syn-cyan' },
		{ name: 'Problem Solving', className: 'text-syn-green' },
		{ name: 'Math', className: 'text-syn-purple' }
	];
</script>

<section id="hero" class="relative grid min-h-screen place-items-center bg-bg">
	<div class="mx-auto w-full max-w-6xl px-6">
		<p class="text-sm text-muted">// A pixel dump by an automaton.</p>

		<h1 class="mt-4 text-5xl font-bold tracking-tight text-fg sm:text-6xl md:text-7xl">
			Arkam <span class="text-syn-purple">Fahri</span>
		</h1>

		<p class="mt-6 max-w-2xl text-base leading-relaxed text-muted">
			I Write Code
		</p>

		<div class="mt-8 flex flex-wrap gap-2">
			{#each skills as skill (skill.name)}
				<span
					class="rounded border border-line bg-panel px-3 py-1 text-sm {skill.className}"
				>
					[ {skill.name} ]
				</span>
			{/each}
		</div>

		<div class="mt-10 flex flex-wrap gap-3">
			<a
				href="#projects"
				rel="external"
				class="rounded bg-accent px-6 py-3 font-mono text-sm font-semibold text-on-accent transition-opacity hover:opacity-90"
			>
				Explore work_
			</a>
			<a
				href="#contact"
				rel="external"
				class="rounded border border-line px-6 py-3 font-mono text-sm text-fg transition-colors hover:border-accent hover:text-accent"
			>
				Say hi
			</a>
		</div>
	</div>
</section>
