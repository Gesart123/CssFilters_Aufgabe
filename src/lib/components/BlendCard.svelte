<script>
	let {
		blendModes = [],
		mixMode = 'multiply',
		bgBlendMode = 'overlay',
		photo = '',
		texture = ''
	} = $props();
</script>

<article
	class="rounded-2xl border border-white/10 bg-white/5 p-6 shadow-xl shadow-purple-500/10 backdrop-blur"
>
	<h2 class="text-xl font-semibold">Blend Mode Demo</h2>
	<p class="mt-2 text-sm text-slate-200">
		<code class="rounded bg-slate-900 px-1 py-0.5 text-[0.9em]">mix-blend-mode</code> mischt
		Vordergrund mit dem darunterliegenden Element.
		<code class="rounded bg-slate-900 px-1 py-0.5 text-[0.9em]">background-blend-mode</code>
		mischt mehrere Hintergründe eines Elements.
	</p>

	<div class="mt-4 grid gap-4 sm:grid-cols-2">
		<label class="grid gap-1 text-sm font-semibold">
			<span>mix-blend-mode</span>
			<select
				class="rounded-lg border border-white/10 bg-slate-900 px-3 py-2 text-sm"
				bind:value={mixMode}
			>
				{#each blendModes as mode (mode)}
					<option value={mode}>{mode}</option>
				{/each}
			</select>
		</label>

		<label class="grid gap-1 text-sm font-semibold">
			<span>background-blend-mode</span>
			<select
				class="rounded-lg border border-white/10 bg-slate-900 px-3 py-2 text-sm"
				bind:value={bgBlendMode}
			>
				{#each blendModes as mode (mode)}
					<option value={mode}>{mode}</option>
				{/each}
			</select>
		</label>
	</div>

	<div class="mt-6 grid gap-6 sm:grid-cols-2">
		<div class="relative overflow-hidden rounded-xl border border-white/10 bg-slate-900/70 p-4">
			<div class="text-xs uppercase tracking-[0.2em] text-indigo-200">
				mix-blend-mode: {mixMode}
			</div>
			<div
				class="mt-3 flex items-center justify-center overflow-hidden rounded-lg bg-gradient-to-br from-indigo-600 via-purple-600 to-amber-500 p-6"
			>
				<img
					src={photo}
					alt="Blend demo"
					class="w-full max-w-xs rounded-lg object-cover shadow-lg"
					style={`mix-blend-mode: ${mixMode};`}
					loading="lazy"
				/>
			</div>
		</div>

		<div class="relative overflow-hidden rounded-xl border border-white/10 bg-slate-900/70 p-4">
			<div class="text-xs uppercase tracking-[0.2em] text-indigo-200">
				background-blend-mode: {bgBlendMode}
			</div>
			<!-- svelte-ignore element_invalid_self_closing_tag -->
			<div
				class="mt-3 aspect-square w-full rounded-lg shadow-lg"
				style={`background-image: linear-gradient(135deg, rgba(79,70,229,0.8), rgba(236,72,153,0.7)), url(${texture}); background-size: cover; background-position: center; background-blend-mode: ${bgBlendMode};`}
			/>
		</div>
	</div>

	<div class="mt-6 grid gap-4 sm:grid-cols-2">
		<div class="rounded-lg bg-slate-900/60 p-4 text-xs font-mono text-indigo-100">
			{`mix-blend-mode: ${mixMode};`}
		</div>
		<div class="rounded-lg bg-slate-900/60 p-4 text-xs font-mono text-indigo-100">
			{`background-blend-mode: ${bgBlendMode};`}
		</div>
	</div>
</article>
