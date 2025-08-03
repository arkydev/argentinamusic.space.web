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

<div class="min-h-screen bg-gray-50 relative"
     style="background-color: #fefbff;"
>

	<main class="relative z-10 lg:min-h-screen lg:flex lg:items-center lg:justify-center px-4 sm:px-6 lg:px-8 py-8 lg:py-8">
		<div class="max-w-4xl mx-auto text-center w-full">
			
			<div class="space-y-8 sm:space-y-12 lg:space-y-20">
				
				<!-- Brand & core message -->
				<div class="space-y-4 sm:space-y-6">
					<h1 class="text-4xl sm:text-5xl md:text-6xl lg:text-7xl font-normal tracking-tight leading-tight"
					    style="font-family: 'Roboto', sans-serif; color: #1c1b1f;">
						Argentina Music
					</h1>
					
					<div class="space-y-3 sm:space-y-4">
						<h2 class="text-2xl sm:text-3xl md:text-4xl lg:text-5xl font-light leading-tight px-4"
						    style="font-family: 'Roboto', sans-serif; color: #49454f;">
							<span class="font-medium" style="color: #6750a4;">
								{actions[currentAction].verb}
							</span>
							<br class="hidden sm:block">
							<span class="sm:ml-0 ml-2">{actions[currentAction].object}</span>
						</h2>
						<p class="text-lg sm:text-xl leading-relaxed max-w-2xl mx-auto px-4"
						   style="font-family: 'Roboto', sans-serif; color: #73777a;">
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
						<div class="rounded-3xl p-4 sm:p-6 space-y-2 sm:space-y-3 transition-all duration-300 hover:shadow-lg"
						     style="background-color: #f7f2fa; border: 1px solid #e6e0e9;">
							<h3 class="font-medium text-sm sm:text-base"
							    style="font-family: 'Roboto', sans-serif; color: #1c1b1f;">{item.title}</h3>
							<p class="text-xs sm:text-sm leading-tight"
							   style="font-family: 'Roboto', sans-serif; color: #49454f;">{item.desc}</p>
						</div>
					{/each}
				</div>

				<!-- Coverage -->
				<div class="space-y-3 sm:space-y-4 px-4">
					<h3 class="text-base sm:text-lg font-medium"
					    style="font-family: 'Roboto', sans-serif; color: #1c1b1f;">
						Cubrimos todo el país
					</h3>
					<div class="flex flex-wrap justify-center gap-x-3 sm:gap-x-4 lg:gap-x-6 gap-y-2 text-xs sm:text-sm">
						{#each ['Buenos Aires', 'Córdoba', 'Rosario', 'Mendoza', 'La Plata', 'Bariloche', 'Tucumán', 'Mar del Plata'] as city}
							<span class="whitespace-nowrap px-3 py-1 rounded-full font-medium"
							      style="background-color: #e8def8; color: #1c1b1f; font-family: 'Roboto', sans-serif;">{city}</span>
						{/each}
					</div>
					<p class="text-xs leading-relaxed px-2"
					   style="font-family: 'Roboto', sans-serif; color: #73777a;">
						Rock • Jazz • Electrónica • Folklore • Tango • Pop • Cumbia • y más
					</p>
				</div>

				<!-- Under construction status -->
				<div class="space-y-4 px-4">
					<div class="rounded-3xl p-6"
					     style="background-color: #f7f2fa; border: 1px solid #e6e0e9;">
						<!-- Gradient line -->
						<div class="h-px mb-4" style="background: linear-gradient(to right, transparent, #6750a4, transparent);"></div>
						
						<!-- Status indicator -->
						<div class="flex items-center justify-center space-x-4">
							<div class="flex items-center space-x-2">
								<div class="relative">
									<div class="w-3 h-3 rounded-full animate-pulse" style="background-color: #6750a4;"></div>
									<div class="absolute inset-0 w-3 h-3 rounded-full animate-ping opacity-75" style="background-color: #6750a4;"></div>
								</div>
								<span class="font-medium text-sm" style="font-family: 'Roboto', sans-serif; color: #1c1b1f;">En desarrollo</span>
							</div>
							<div class="w-px h-6" style="background-color: #cac4d0;"></div>
							<div class="text-xs font-medium uppercase" style="font-family: 'Roboto', sans-serif; color: #49454f;">
								Próximamente 2025
							</div>
						</div>
						
						<!-- Progress visualization -->
						<div class="mt-4 max-w-xs mx-auto">
							<div class="flex items-center justify-center space-x-1">
								{#each Array(5) as _, i}
									<div class="h-1 w-8 rounded-full" style="background-color: #e6e0e9;">
										<div 
											class="h-full rounded-full transition-all duration-1000"
											style="background-color: #6750a4; width: {i < 3 ? '100%' : i === 3 ? '60%' : '0%'};"
										></div>
									</div>
								{/each}
							</div>
							<p class="text-center text-xs mt-3" style="font-family: 'Roboto', sans-serif; color: #73777a;">
								Creando experiencias únicas
							</p>
						</div>
					</div>
				</div>

			</div>

		</div>
	</main>
</div>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@100;300;400;500;700;900&display=swap');
	
	:global(body) {
		font-family: 'Roboto', sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
	}
</style>
