<script>
	import { onMount } from 'svelte';

	let currentAction = $state(0);
	let mounted = $state(false);

	const actions = [
		{ verb: 'explorás', object: 'la escena completa' },
		{ verb: 'descubrís', object: 'quién toca hoy' },
		{ verb: 'seguís', object: 'toda la movida' },
		{ verb: 'conectás', object: 'con la música' }
	];

	onMount(() => {
		mounted = true;
		const actionInterval = setInterval(() => {
			currentAction = (currentAction + 1) % actions.length;
		}, 3200);

		return () => clearInterval(actionInterval);
	});
</script>

<svelte:head>
	<title>Argentina Music Space</title>
	<meta name="description" content="Plataforma de descubrimiento musical para Argentina" />
</svelte:head>

<div class="h-screen bg-stone-50 relative overflow-hidden">
	<!-- Subtle noise texture -->
	<div class="absolute inset-0 opacity-[0.03]" style="background-image: url('data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjAwIiBoZWlnaHQ9IjIwMCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZGVmcz4KICAgIDxmaWx0ZXIgaWQ9Im5vaXNlIj4KICAgICAgPGZlVHVyYnVsZW5jZSB0eXBlPSJmcmFjdGFsTm9pc2UiIGJhc2VGcmVxdW5jeT0iMC45IiBudW1PY3RhdmVzPSI0IiBzdGl0Y2hUaWxlcz0ic3RpdGNoIi8+CiAgICA8L2ZpbHRlcj4KICA8L2RlZnM+CiAgPHJlY3Qgd2lkdGg9IjEwMCUiIGhlaWdodD0iMTAwJSIgZmlsdGVyPSJ1cmwoI25vaXNlKSIgb3BhY2l0eT0iMC4xIi8+Cjwvc3ZnPgo=')"></div>

	<main class="relative z-10 min-h-screen flex items-center justify-center px-4 sm:px-6 lg:px-8 py-8 sm:py-12">
		<div class="max-w-4xl mx-auto text-center w-full">
			
			<div class="space-y-12 sm:space-y-16 lg:space-y-20">
				
				<!-- Brand & core message -->
				<div class="space-y-6 sm:space-y-8">
					<h1 class="text-4xl sm:text-5xl md:text-6xl lg:text-7xl font-light text-stone-900 tracking-tight leading-tight">
						Argentina Music
					</h1>
					
					<div class="space-y-4 sm:space-y-6">
						<h2 class="text-2xl sm:text-3xl md:text-4xl lg:text-5xl font-light text-stone-800 leading-tight px-4">
							<span class="text-stone-900 font-medium border-b-2 border-stone-300">
								{actions[currentAction].verb}
							</span>
							<br class="hidden sm:block">
							<span class="sm:ml-0 ml-2">{actions[currentAction].object}</span>
						</h2>
						<p class="text-lg sm:text-xl text-stone-600 leading-relaxed max-w-2xl mx-auto px-4">
							Reunimos toda la información musical del país: fechas, lugares, artistas y precios
						</p>
					</div>
				</div>

				<!-- What we aggregate -->
				<div class="grid grid-cols-2 sm:grid-cols-2 lg:grid-cols-4 gap-4 sm:gap-6 lg:gap-8 text-center px-4">
					{#each [
						{ title: 'Conciertos', desc: 'Fechas y venues' },
						{ title: 'Festivales', desc: 'Lineups completos' },
						{ title: 'Artistas', desc: 'Tours y shows' },
						{ title: 'Precios', desc: 'Info de entradas' }
					] as item}
						<div class="space-y-2 sm:space-y-3">
							<h3 class="font-medium text-stone-900 text-sm sm:text-base">{item.title}</h3>
							<p class="text-xs sm:text-sm text-stone-600 leading-tight">{item.desc}</p>
						</div>
					{/each}
				</div>

				<!-- Coverage -->
				<div class="space-y-4 sm:space-y-6 px-4">
					<h3 class="text-base sm:text-lg font-medium text-stone-800">
						Cubrimos todo el territorio
					</h3>
					<div class="flex flex-wrap justify-center gap-x-4 sm:gap-x-6 lg:gap-x-8 gap-y-2 text-stone-600 text-xs sm:text-sm">
						{#each ['Buenos Aires', 'Córdoba', 'Rosario', 'Mendoza', 'La Plata', 'Bariloche', 'Tucumán', 'Mar del Plata'] as city}
							<span class="whitespace-nowrap">{city}</span>
						{/each}
					</div>
					<p class="text-xs text-stone-500 leading-relaxed px-2">
						Rock • Jazz • Electrónica • Folklore • Tango • Pop • Cumbia • y más
					</p>
				</div>

				<!-- CTA -->
				<div class="space-y-3 sm:space-y-4 px-4">
					<button class="bg-stone-900 text-stone-50 px-8 sm:px-10 py-3 sm:py-4 font-medium hover:bg-stone-800 transition-colors text-sm sm:text-base w-full sm:w-auto">
						Quiero estar al día
					</button>
					<div class="flex items-center justify-center space-x-2 text-stone-400 text-xs sm:text-sm px-2">
						<div class="w-2 h-2 bg-blue-500 rounded-full animate-pulse flex-shrink-0"></div>
						<span class="text-center leading-tight">Armando la base de datos más completa</span>
					</div>
				</div>

			</div>

		</div>
	</main>
</div>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap');
	
	:global(body) {
		font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
	}
</style>
