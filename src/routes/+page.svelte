<script>
	import BlendCard from '$lib/components/BlendCard.svelte';
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
				Playground fuer Blur, Kontrast, Helligkeit, Grayscale & Blend Modes
			</h1>
			<p class="max-w-3xl text-base text-slate-200">
				Steuere mit einfachen Reglern die CSS
				<code class="rounded bg-slate-900 px-1 py-0.5 text-[0.9em]">filter</code>-Property und
				probiere verschiedene
				<code class="rounded bg-slate-900 px-1 py-0.5 text-[0.9em]">mix/background-blend-mode</code>
				Werte aus.
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

			<BlendCard {photo} {texture} {blendModes} bind:mixMode bind:bgBlendMode />
		</section>

		<section
			class="rounded-2xl border border-white/10 bg-white/5 p-6 shadow-lg shadow-slate-900/40 backdrop-blur"
		>
			<h3 class="text-lg font-semibold">Mini-Tutorial (60 Minuten Uebung)</h3>
			<ol class="mt-3 list-decimal space-y-2 pl-5 text-sm text-slate-200">
				<li>Baue eine einfache Seite mit einem Bild und einem Range-Slider.</li>
				<li>
					Binde den Slider mit <code class="rounded bg-slate-900 px-1 py-0.5 text-[0.9em]"
						>bind:value</code
					>
					an eine Variable <code class="rounded bg-slate-900 px-1 py-0.5 text-[0.9em]">blur</code>.
				</li>
				<li>
					Setze
					<code class="rounded bg-slate-900 px-1 py-0.5 text-[0.9em]"
						>style={`filter: blur(${'{'}blur{'}'})`}</code
					>
					auf das Bild.
				</li>
				<li>Fuege weitere Slider fuer Kontrast, Helligkeit, Grayscale hinzu.</li>
				<li>
					Erzeuge eine zweite Karte mit zwei Hintergruenden (Gradient + Bild) und wende
					<code class="rounded bg-slate-900 px-1 py-0.5 text-[0.9em]">background-blend-mode</code> an.
				</li>
				<li>Teste verschiedene Blend Modes ueber ein Select; notiere Effekte fuer das Handout.</li>
				<li>Screenshot der wichtigsten Zustaende fuer Praesentation/Handout machen.</li>
			</ol>
		</section>
	</section>
</main>
