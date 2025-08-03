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
     style="background: linear-gradient(135deg, #f0f9ff 0%, #fef3c7 50%, #f0f9ff 100%);"
>

	<main class="relative z-10 lg:min-h-screen lg:flex lg:items-center lg:justify-center px-4 sm:px-6 lg:px-8 py-8 lg:py-4">
		<div class="max-w-4xl mx-auto text-center w-full">
			
			<div class="space-y-6 sm:space-y-8 lg:space-y-8">
				
				<!-- Brand & core message -->
				<div class="space-y-3 sm:space-y-4 lg:space-y-3">
					<h1 class="text-4xl sm:text-5xl md:text-6xl lg:text-6xl font-light tracking-tight leading-tight"
					    style="font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif; color: #0f172a;">
						Argentina Music
					</h1>
					
					<div class="space-y-2 sm:space-y-3 lg:space-y-2">
						<h2 class="text-2xl sm:text-3xl md:text-4xl lg:text-4xl font-light leading-tight px-4"
						    style="font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif; color: #334155;">
							<span class="font-medium" style="color: #0ea5e9;">
								{actions[currentAction].verb}
							</span>
							<br class="hidden sm:block">
							<span class="sm:ml-0 ml-2">{actions[currentAction].object}</span>
						</h2>
						<p class="text-base sm:text-lg lg:text-lg leading-relaxed max-w-2xl mx-auto px-4"
						   style="font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif; color: #64748b;">
							Reunimos toda la información musical del país: fechas, lugares, artistas y precios
						</p>
					</div>
				</div>

				<!-- What we aggregate -->
				<div class="grid grid-cols-2 sm:grid-cols-2 lg:grid-cols-4 gap-3 sm:gap-4 lg:gap-4 text-center px-4">
					{#each [
						{ title: 'Conciertos', desc: 'Fechas y venues' },
						{ title: 'Festivales', desc: 'Lineups completos' },
						{ title: 'Artistas', desc: 'Tours y shows' },
						{ title: 'Precios', desc: 'Info de entradas' }
					] as item}
						<div class="rounded-3xl p-3 sm:p-4 lg:p-4 space-y-1 sm:space-y-2 transition-all duration-300 hover:shadow-lg"
						     style="background-color: #f8fafc; border: 1px solid #e2e8f0;">
							<h3 class="font-medium text-sm sm:text-base"
							    style="font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif; color: #0f172a;">{item.title}</h3>
							<p class="text-xs sm:text-sm leading-tight"
							   style="font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif; color: #64748b;">{item.desc}</p>
						</div>
					{/each}
				</div>

				<!-- Coverage -->
				<div class="space-y-2 sm:space-y-3 lg:space-y-2 px-4">
					<h3 class="text-base sm:text-lg font-medium"
					    style="font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif; color: #0f172a;">
						Cubrimos todo el país
					</h3>
					<div class="flex flex-wrap justify-center gap-x-2 sm:gap-x-3 lg:gap-x-3 gap-y-1 text-xs sm:text-sm">
						{#each ['Buenos Aires', 'Córdoba', 'Rosario', 'Mendoza', 'La Plata', 'Bariloche', 'Tucumán', 'Mar del Plata'] as city}
							<span class="whitespace-nowrap px-2 py-1 rounded-full font-medium text-xs"
							      style="background-color: #fef3c7; color: #059669; font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;">{city}</span>
						{/each}
					</div>
					<p class="text-xs leading-relaxed px-2 lg:text-xs lg:mt-1"
					   style="font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif; color: #64748b;">
						Rock • Jazz • Electrónica • Folklore • Tango • Pop • Cumbia • y más
					</p>
				</div>

				<!-- Under construction status -->
				<div class="space-y-3 lg:space-y-2 px-4">
					<div class="rounded-3xl p-4 lg:p-4"
					     style="background-color: #f1f5f9; border: 1px solid #cbd5e1;">
						<!-- Gradient line -->
						<div class="h-px mb-3 lg:mb-2" style="background: linear-gradient(to right, transparent, #0ea5e9, transparent);"></div>
						
						<!-- Status indicator -->
						<div class="flex items-center justify-center space-x-4">
							<div class="flex items-center space-x-2">
								<div class="relative">
									<div class="w-3 h-3 rounded-full animate-pulse" style="background-color: #0ea5e9;"></div>
									<div class="absolute inset-0 w-3 h-3 rounded-full animate-ping opacity-75" style="background-color: #0ea5e9;"></div>
								</div>
								<span class="font-medium text-sm" style="font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif; color: #0f172a;">En desarrollo</span>
							</div>
							<div class="w-px h-6" style="background-color: #cbd5e1;"></div>
							<div class="text-xs font-medium uppercase" style="font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif; color: #334155;">
								Próximamente 2025
							</div>
						</div>
						
						<!-- Progress visualization -->
						<div class="mt-3 lg:mt-2 max-w-xs mx-auto">
							<div class="flex items-center justify-center space-x-1">
								{#each Array(5) as _, i}
									<div class="h-1 w-8 rounded-full" style="background-color: #e2e8f0;">
										<div 
											class="h-full rounded-full transition-all duration-1000"
											style="background-color: #0ea5e9; width: {i < 3 ? '100%' : i === 3 ? '60%' : '0%'};"
										></div>
									</div>
								{/each}
							</div>
							<p class="text-center text-xs mt-2 lg:mt-1" style="font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif; color: #64748b;">
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
	@import url('https://fonts.googleapis.com/css2?family=Inter:wght@100;200;300;400;500;600;700;800;900&display=swap');
	
	:global(body) {
		font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		letter-spacing: -0.01em;
	}
</style>
