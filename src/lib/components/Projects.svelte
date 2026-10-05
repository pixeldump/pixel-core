<script lang="ts">
	type Project = {
		name: string;
		description: string;
		stack: string[];
		href?: string;
		file: string;
		accent: string;
		dot: string;
	};

	const projects: Project[] = [
		{
			name: 'Pixel Core',
			description: 'The site you are browsing right now, an anti-portfolio of everything I have not built.',
			stack: ['Svelte', 'Typescript', 'Tailwind'],
			file: 'pixel-core.svelte',
			accent: 'text-syn-green',
			dot: 'bg-syn-green'
		},
		{
			name: 'Pixel Dump',
			description:
				'A technical and satirical blog, every brain dump I have written, strewn across a knowledge garden of everything I know.',
			stack: ['Obsidian', 'Quartz'],
			file: 'pixel-dump.md',
			accent: 'text-syn-purple',
			dot: 'bg-syn-purple'
		},
		{
			name: 'Bastion Cache',
			description: 'A stupidly simple but extremely robust cache implementation in pure Go.',
			stack: ['Go', 'Redis'],
			file: 'bastioncache.go',
			accent: 'text-syn-red',
			dot: 'bg-syn-red'
		}
	];
</script>

<section id="projects" class="border-t border-line bg-bg py-20">
	<div class="mx-auto max-w-6xl px-6">
		<h2 class="text-sm text-muted">
			<span class="text-syn-green">02</span> // projects
		</h2>
		<p class="mt-4 text-3xl font-semibold tracking-tight text-fg sm:text-4xl">
			Artifacts from the Lab.
		</p>

		<div class="mt-10 grid gap-5 md:grid-cols-2 lg:grid-cols-3">
			{#each projects as project, index (project.name)}
				<article
					class="group flex flex-col overflow-hidden rounded border border-line bg-panel transition-colors hover:border-accent"
				>
					<div class="flex items-center justify-between border-b border-line bg-bg px-4 py-2">
						<span class="flex min-w-0 items-center gap-2">
							<span class={`h-2 w-2 shrink-0 ${project.dot}`}></span>
							<span class="truncate text-xs text-muted">{project.file}</span>
						</span>
						<span class="text-xs text-muted">L{index + 1}</span>
					</div>

					<div class="flex flex-1 flex-col p-5">
						{#if project.href}
							<a
								href={project.href}
								rel="external"
								class="text-sm font-bold text-fg transition-colors group-hover:text-accent"
							>
								{project.name}
							</a>
						{:else}
							<h3
								class="text-sm font-bold text-fg transition-colors group-hover:text-accent"
							>
								{project.name}
							</h3>
						{/if}
						<p class="mt-3 flex-1 text-sm leading-relaxed text-muted">
							{project.description}
						</p>
						<div class="flex flex-wrap gap-x-2 gap-y-1 pt-5">
							{#each project.stack as tech (tech)}
								<span class="text-xs {project.accent}">&gt; {tech}</span>
							{/each}
						</div>
					</div>
				</article>
			{/each}
		</div>
	</div>
</section>
