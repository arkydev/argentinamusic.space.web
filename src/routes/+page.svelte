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
	<title>Argentina Music Space - Descubrí Conciertos, Festivales y Música en Argentina</title>
	<meta name="description" content="Descubrí toda la escena musical argentina: conciertos, festivales, artistas y precios de entradas en Buenos Aires, Córdoba, Rosario y más ciudades. Rock, jazz, folklore, tango y todos los géneros." />
	<meta name="keywords" content="conciertos Argentina, festivales música Argentina, música Buenos Aires, shows Córdoba, eventos musicales Rosario, rock argentino, jazz Argentina, folklore, tango, música en vivo" />
	<meta name="author" content="Argentina Music Space" />
	<meta name="robots" content="index, follow" />
	<meta property="og:title" content="Argentina Music Space - Descubrí toda la música argentina" />
	<meta property="og:description" content="La plataforma completa para descubrir conciertos, festivales y artistas en Argentina. Información de eventos musicales en todas las ciudades principales." />
	<meta property="og:type" content="website" />
	<meta property="og:locale" content="es_AR" />
	<meta name="twitter:card" content="summary_large_image" />
	<meta name="twitter:title" content="Argentina Music Space - Descubrí toda la música argentina" />
	<meta name="twitter:description" content="Conciertos, festivales y música en vivo en Argentina. Toda la información de eventos musicales en un solo lugar." />
	<link rel="canonical" href="https://argentinamusicspace.com" />
	<script type="application/ld+json">
		{
			"@context": "https://schema.org",
			"@type": "WebSite",
			"name": "Argentina Music Space",
			"description": "Plataforma de descubrimiento musical para Argentina",
			"url": "https://argentinamusicspace.com",
			"inLanguage": "es-AR",
			"about": {
				"@type": "Thing",
				"name": "Música Argentina",
				"description": "Escena musical argentina incluyendo conciertos, festivales y artistas"
			},
			"audience": {
				"@type": "Audience",
				"geographicArea": {
					"@type": "Country",
					"name": "Argentina"
				}
			},
			"genre": ["Rock", "Jazz", "Electrónica", "Folklore", "Tango", "Pop", "Cumbia"],
			"areaServed": [
				{
					"@type": "City",
					"name": "Buenos Aires",
					"addressCountry": "AR"
				},
				{
					"@type": "City", 
					"name": "Córdoba",
					"addressCountry": "AR"
				},
				{
					"@type": "City",
					"name": "Rosario", 
					"addressCountry": "AR"
				},
				{
					"@type": "City",
					"name": "Mendoza",
					"addressCountry": "AR"
				}
			]
		}
	</script>
</svelte:head>

<div class="min-h-screen relative"
     style="background: linear-gradient(135deg, #fafcff 0%, #fefffe 50%, #fafcff 100%);"
>

	<main class="relative z-10 lg:flex lg:items-center lg:justify-center px-4 sm:px-6 lg:px-8 py-8 lg:py-4 lg:min-h-[calc(100vh-120px)]">
		<div class="max-w-4xl mx-auto text-center w-full">
			
			<div class="space-y-6 sm:space-y-8 lg:space-y-8">
				
				<!-- Brand & core message -->
				<div class="space-y-3 sm:space-y-4 lg:space-y-3">
					<h1 class="text-4xl sm:text-5xl md:text-6xl lg:text-6xl font-light tracking-tight leading-tight"
					    style="font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif; color: #2d3748;">
						Argentina Music
					</h1>
					
					<div class="space-y-2 sm:space-y-3 lg:space-y-2">
						<h2 class="text-2xl sm:text-3xl md:text-4xl lg:text-4xl font-light leading-tight px-4"
						    style="font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif; color: #4a5568;">
							<span class="font-medium" style="color: #4299e1;">
								{actions[currentAction].verb}
							</span>
							<br class="hidden sm:block">
							<span class="sm:ml-0 ml-2">{actions[currentAction].object}</span>
						</h2>
					</div>
				</div>

				<!-- What we aggregate -->
				<section class="grid grid-cols-2 sm:grid-cols-2 lg:grid-cols-4 gap-3 sm:gap-4 lg:gap-4 text-center px-4" aria-label="Servicios de aggregación musical">
					{#each [
						{ title: 'Conciertos', desc: 'Fechas y venues', bg: '#f0f9ff', border: '#e0f2fe' },
						{ title: 'Festivales', desc: 'Lineups completos', bg: '#fefce8', border: '#fef3c7' },
						{ title: 'Artistas', desc: 'Tours y shows', bg: '#f0fdf4', border: '#dcfce7' },
						{ title: 'Precios', desc: 'Info de entradas', bg: '#fdf2f8', border: '#fce7f3' }
					] as item}
						<article class="rounded-3xl p-3 sm:p-4 lg:p-4 space-y-1 sm:space-y-2 transition-all duration-300 hover:shadow-lg hover:scale-102"
						     style="background: {item.bg}; border: 1px solid {item.border}; box-shadow: 0 2px 6px rgba(0,0,0,0.06);">
							<h3 class="font-medium text-sm sm:text-base"
							    style="font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif; color: #2d3748;">{item.title}</h3>
							<p class="text-xs sm:text-sm leading-tight"
							   style="font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif; color: #718096;">{item.desc}</p>
						</article>
					{/each}
				</section>

				<!-- Music genres -->
				<section class="space-y-3 sm:space-y-4 lg:space-y-3 px-4" aria-label="Géneros musicales">
					<div class="flex flex-wrap justify-center gap-x-3 sm:gap-x-4 lg:gap-x-4 gap-y-2 text-sm sm:text-base">
						{#each [
							{ name: 'Rock', bg: '#fef2f2', color: '#991b1b' },
							{ name: 'Jazz', bg: '#f0f9ff', color: '#1e40af' },
							{ name: 'Electrónica', bg: '#f0fdf4', color: '#166534' },
							{ name: 'Folklore', bg: '#fefce8', color: '#a16207' },
							{ name: 'Tango', bg: '#fdf2f8', color: '#9d174d' },
							{ name: 'Pop', bg: '#f3e8ff', color: '#7c2d12' },
							{ name: 'Cumbia', bg: '#ecfdf5', color: '#047857' }
						] as genre}
							<span class="whitespace-nowrap px-3 py-2 rounded-full font-medium transition-all duration-300 hover:scale-105"
							      style="background: {genre.bg}; color: {genre.color}; font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif; box-shadow: 0 1px 3px rgba(0,0,0,0.08); border: 1px solid rgba(0,0,0,0.05);">{genre.name}</span>
						{/each}
					</div>
				</section>

				<!-- Coverage -->
				<section class="px-4" aria-label="Ciudades cubiertas">
					<div class="flex flex-wrap justify-center gap-x-3 sm:gap-x-4 lg:gap-x-4 gap-y-2 text-xs sm:text-sm">
						{#each [
							{ name: 'Buenos Aires', bg: '#e6f3ff', color: '#2d3748' },
							{ name: 'Córdoba', bg: '#fff7e6', color: '#2d3748' },
							{ name: 'Rosario', bg: '#e6ffe6', color: '#2d3748' },
							{ name: 'Mendoza', bg: '#ffe6f0', color: '#2d3748' },
							{ name: 'La Plata', bg: '#f3e6ff', color: '#2d3748' },
							{ name: 'Bariloche', bg: '#e6ffff', color: '#2d3748' },
							{ name: 'Tucumán', bg: '#f0ffe6', color: '#2d3748' },
							{ name: 'Mar del Plata', bg: '#ffe6e6', color: '#2d3748' }
						] as city}
							<span class="whitespace-nowrap px-3 py-2 rounded-full font-medium text-xs transition-all duration-300 hover:scale-105"
							      style="background: {city.bg}; color: {city.color}; font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif; box-shadow: 0 1px 3px rgba(0,0,0,0.08); border: 1px solid rgba(0,0,0,0.05);">{city.name}</span>
						{/each}
					</div>
				</section>

			</div>

		</div>
	</main>

	<!-- Under construction status - Fixed at bottom -->
	<footer class="relative z-10 px-4 sm:px-6 lg:px-8 pb-8">
		<div class="max-w-2xl mx-auto">
			<div class="rounded-3xl p-4 lg:p-4"
			     style="background: #fafcff; border: 1px solid #e2e8f0; box-shadow: 0 2px 8px rgba(0,0,0,0.06);">
				<!-- Gradient line -->
				<div class="h-px mb-3 lg:mb-2" style="background: linear-gradient(to right, transparent, #cbd5e0, transparent);"></div>
				
				<!-- Status indicator -->
				<div class="flex items-center justify-center space-x-4">
					<div class="flex items-center space-x-2">
						<div class="relative">
							<div class="w-3 h-3 rounded-full animate-pulse" style="background-color: #a7d8ea;"></div>
							<div class="absolute inset-0 w-3 h-3 rounded-full animate-ping opacity-75" style="background-color: #a7d8ea;"></div>
						</div>
						<span class="font-medium text-sm" style="font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif; color: #2d3748;">En desarrollo</span>
					</div>
					<div class="w-px h-6" style="background-color: #e2e8f0;"></div>
					<div class="text-xs font-medium uppercase" style="font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif; color: #718096;">
						Próximamente Q4 2025
					</div>
				</div>
				
				<!-- Progress visualization -->
				<div class="mt-3 lg:mt-2 max-w-xs mx-auto">
					<div class="flex items-center justify-center space-x-1">
						{#each Array(5) as _, i}
							<div class="h-1 w-8 rounded-full" style="background-color: #f1f5f9;">
								<div 
									class="h-full rounded-full transition-all duration-1000"
									style="background-color: #a7d8ea; width: {i < 3 ? '100%' : i === 3 ? '60%' : '0%'};"
								></div>
							</div>
						{/each}
					</div>
					<p class="text-center text-xs mt-2 lg:mt-1" style="font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif; color: #718096;">
						Creando experiencias únicas
					</p>
				</div>
			</div>
		</div>
	</footer>
</div>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Inter:wght@100;200;300;400;500;600;700;800;900&display=swap');
	
	:global(body) {
		font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		letter-spacing: -0.01em;
	}
</style>
