<script>
	import FilterCard from '$lib/components/FilterCard.svelte';

	let blur = 8;
	let contrast = 100;
	let brightness = 100;
	let grayscale = 0;

	const blendModes = [
		'normal',
		'multiply',
		'screen',
		'overlay',
		'darken',
		'lighten',
		'difference',
		'luminosity'
	];
	let mixMode = 'multiply';
	let bgBlendMode = 'overlay';

	const photo =
		'https://images.unsplash.com/photo-1504198453319-5ce911bafcde?w=900&auto=format&fit=crop&q=80';
	const texture =
		'https://images.unsplash.com/photo-1505761671935-60b3a7427bad?w=1200&auto=format&fit=crop&q=80';

	const resetFilters = () => {
		blur = 8;
		contrast = 100;
		brightness = 100;
		grayscale = 0;
	};
</script>

<main class="min-h-screen bg-slate-950 text-slate-50">
	<section class="mx-auto flex max-w-6xl flex-col gap-10 px-4 py-12 sm:px-8">
		<header class="space-y-3">
			<p class="text-sm font-semibold uppercase tracking-[0.2em] text-indigo-300">
				CSS Filters & Blend Modes
			</p>
			<h1 class="text-3xl font-bold sm:text-4xl">
				Playground für Blur, Kontrast, Helligkeit, Grayscale & Blend Modes
			</h1>
			<p class="max-w-3xl text-base text-slate-200">
				Steuere mit einfachen Reglern die CSS <code
					class="rounded bg-slate-900 px-1 py-0.5 text-[0.9em]">filter</code
				>-Property und probiere verschiedene
				<code class="rounded bg-slate-900 px-1 py-0.5 text-[0.9em]">mix/background-blend-mode</code> Werte
				aus.
			</p>
		</header>

		<section class="grid gap-8 lg:grid-cols-2">
			<FilterCard
				{photo}
				bind:blur
				bind:contrast
				bind:brightness
				bind:grayscale
				onReset={resetFilters}
			/>

			<article
				class="rounded-2xl border border-white/10 bg-white/5 p-6 shadow-xl shadow-purple-500/10 backdrop-blur"
			>
				<h2 class="text-xl font-semibold">Blend Mode Demo</h2>
				<p class="mt-2 text-sm text-slate-200">
					<code class="rounded bg-slate-900 px-1 py-0.5 text-[0.9em]">mix-blend-mode</code> mischt
					Vordergrund mit dem darunterliegenden Element.
					<code class="rounded bg-slate-900 px-1 py-0.5 text-[0.9em]">background-blend-mode</code> mischt
					mehrere Hintergründe eines Elements.
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
					<div
						class="relative overflow-hidden rounded-xl border border-white/10 bg-slate-900/70 p-4"
					>
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

					<div
						class="relative overflow-hidden rounded-xl border border-white/10 bg-slate-900/70 p-4"
					>
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
		</section>

		<section
			class="rounded-2xl border border-white/10 bg-white/5 p-6 shadow-lg shadow-slate-900/40 backdrop-blur"
		>
			<h3 class="text-lg font-semibold">Mini-Tutorial (60 Minuten Übung)</h3>
			<ol class="mt-3 list-decimal space-y-2 pl-5 text-sm text-slate-200">
				<li>Baue eine einfache Seite mit einem Bild und einem Range-Slider.</li>
				<li>
					Binde den Slider mit <code class="rounded bg-slate-900 px-1 py-0.5 text-[0.9em]"
						>bind:value</code
					>
					an eine Variable <code class="rounded bg-slate-900 px-1 py-0.5 text-[0.9em]">blur</code>.
				</li>
				<li>
					Setze <code class="rounded bg-slate-900 px-1 py-0.5 text-[0.9em]"
						>style={`filter: blur(${'{'}blur{'}'})`}</code
					> auf das Bild.
				</li>
				<li>Füge weitere Slider für Kontrast, Helligkeit, Grayscale hinzu.</li>
				<li>
					Erzeuge eine zweite Karte mit zwei Hintergründen (Gradient + Bild) und wende <code
						class="rounded bg-slate-900 px-1 py-0.5 text-[0.9em]">background-blend-mode</code
					> an.
				</li>
				<li>Teste verschiedene Blend Modes über ein Select; notiere Effekte für das Handout.</li>
				<li>Screenshot der wichtigsten Zustände für Präsentation/Handout machen.</li>
			</ol>
		</section>
	</section>
</main>
