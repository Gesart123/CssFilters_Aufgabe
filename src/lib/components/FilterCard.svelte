<script>
	export let photo = '';
	export let blur = 8;
	export let contrast = 100;
	export let brightness = 100;
	export let grayscale = 0;
	export let onReset = () => {};
</script>

<article
	class="rounded-2xl border border-white/10 bg-white/5 p-6 shadow-xl shadow-indigo-500/10 backdrop-blur"
>
	<div class="flex items-center justify-between gap-4">
		<h2 class="text-xl font-semibold">Filter Demo</h2>
		<button
			class="rounded-lg bg-indigo-500 px-3 py-1.5 text-sm font-semibold text-white hover:bg-indigo-400"
			onclick={onReset}
		>
			Reset
		</button>
	</div>
	<p class="mt-2 text-sm text-slate-200">
		Filter werden von links nach rechts angewendet. Passe die Regler an und beobachte den Effekt.
	</p>

	<div class="mt-6 overflow-hidden rounded-xl border border-white/10 bg-slate-900">
		<img
			class="aspect-video w-full object-cover transition duration-300"
			src={photo}
			alt="Portrait for filter demo"
			style={`filter: blur(${blur}px) contrast(${contrast}%) brightness(${brightness}%) grayscale(${grayscale}%);`}
			loading="lazy"
		/>
	</div>

	<div class="mt-6 space-y-4">
		<label class="grid gap-1 text-sm font-semibold">
			<span>Blur ({blur}px)</span>
			<input class="accent-indigo-400" type="range" min="0" max="20" step="1" bind:value={blur} />
		</label>
		<label class="grid gap-1 text-sm font-semibold">
			<span>Kontrast ({contrast}%)</span>
			<input
				class="accent-indigo-400"
				type="range"
				min="50"
				max="200"
				step="1"
				bind:value={contrast}
			/>
		</label>
		<label class="grid gap-1 text-sm font-semibold">
			<span>Helligkeit ({brightness}%)</span>
			<input
				class="accent-indigo-400"
				type="range"
				min="50"
				max="200"
				step="1"
				bind:value={brightness}
			/>
		</label>
		<label class="grid gap-1 text-sm font-semibold">
			<span>Grayscale ({grayscale}%)</span>
			<input
				class="accent-indigo-400"
				type="range"
				min="0"
				max="100"
				step="1"
				bind:value={grayscale}
			/>
		</label>
	</div>

	<div class="mt-6 rounded-lg bg-slate-900/60 p-4 text-xs font-mono text-indigo-100">
		filter: blur({blur}px) contrast({contrast}%) brightness({brightness}%) grayscale({grayscale}%);
	</div>
</article>
