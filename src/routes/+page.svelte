<script lang="ts">
	type Product = {
		id: number;
		name: string;
		price: number;
		image: string;
	};

	type CartItem = {
		id: number;
		productId: number;
		name: string;
		price: number;
	};

	const PRODUCTS: Product[] = [
		{ id: 1, name: 'manzana', price: 1, image: '/images/manzana.jpg' },
		{ id: 2, name: 'pera', price: 1.5, image: '/images/pera.jpg' },
		{ id: 3, name: 'uva', price: 2.5, image: '/images/uva.jpg' },
		{ id: 4, name: 'sandía', price: 6, image: '/images/sandia.jpg' },
		{ id: 5, name: 'kiwi', price: 3.8, image: '/images/kiwi.jpg' }
	];

	let cart: CartItem[] = [];
	let nextCartItemId = 1;

	function addToCart(product: Product): void {
		cart = [
			...cart,
			{
				id: nextCartItemId++,
				productId: product.id,
				name: product.name,
				price: product.price
			}
		];
	}

	$: total = cart.reduce((sum, item) => sum + item.price, 0);

	function removeFromCart(itemId: number): void {
		cart = cart.filter((item) => item.id !== itemId);
	}
</script>

<main class="container mx-auto max-w-7xl p-4">
	<header class="mb-8">
		<h1 class="text-3xl font-bold">Frutería</h1>
	</header>

	<div class="grid gap-8 lg:grid-cols-3">
		<section class="lg:col-span-2">
			<h2 class="mb-6 text-2xl font-semibold">Productos Disponibles</h2>
			<ul class="grid gap-4 sm:grid-cols-2 md:grid-cols-3">
				{#each PRODUCTS as product}
					<li>
						<article
							class="overflow-hidden rounded-lg border bg-white"
						>
							<figure class="relative h-48 bg-gray-200">
								<img src={product.image} alt={product.name} class="h-full w-full object-cover" />
							</figure>

							<div class="p-4">
								<h3 class="mb-1 text-lg font-bold">{product.name}</h3>
								<p class="mb-3 text-xl font-bold text-green-600">
									{product.price.toFixed(2)}€
									<span class="text-sm text-gray-500">/ud.</span>
								</p>

								<div class="mb-3 flex items-center justify-between">
									<span class="text-sm font-medium">Cantidad:</span>
									<div
										class="flex items-center gap-2"
										role="group"
									>
										<button
											class="flex h-8 w-8 items-center justify-center rounded-lg bg-orange-400 font-bold text-white transition hover:bg-orange-500"
										>
											−
										</button>
										<output class="w-8 text-center font-semibold" aria-live="polite"> </output>
										<button
											class="flex h-8 w-8 items-center justify-center rounded-lg bg-orange-400 font-bold text-white transition hover:bg-orange-500"
										>
											+
										</button>
									</div>
								</div>

								<button
									on:click={() => addToCart(product)}
									class="w-full rounded-lg bg-green-600 py-2 font-semibold text-white transition hover:bg-green-700"
								>
									Añadir al Carrito
								</button>
							</div>
						</article>
					</li>
				{/each}
			</ul>
		</section>

		<aside class="lg:col-span-1">
			<div class="sticky top-4 rounded-lg bg-white p-6 shadow-md">
				<h2 class="mb-4 text-2xl font-semibold">Ticket</h2>

				{#if cart.length === 0}
					<p class="py-8 text-center text-gray-500">El carrito está vacío</p>
				{:else}
					<ul class="mb-6 space-y-3">
						{#each cart as item (item.id)}
							<li class="flex items-start justify-between rounded-lg border bg-gray-50 p-3">
								<div class="flex-1">
									<p class="font-medium">{item.name}</p>
									<p class="text-sm text-gray-600">
										{item.price.toFixed(2)}€
									</p>
									<p class="mt-1 text-sm font-semibold text-green-600">
										{item.price.toFixed(2)}€
									</p>
								</div>
								<button
									on:click={() => removeFromCart(item.id)}
									class="ml-2 rounded bg-red-500 px-3 py-1 text-sm text-white transition hover:bg-red-600"
									aria-label="Eliminar una unidad de {item.name}"
								>
									Eliminar
								</button>
							</li>
						{/each}
					</ul>

					<footer class="border-t-2 border-gray-300 pt-4">
						<div class="flex items-center justify-between">
							<span class="text-xl font-bold">Total:</span>
							<output class="text-3xl font-bold text-green-600" aria-live="polite">
								{total.toFixed(2)} €
							</output>
						</div>
					</footer>
				{/if}
			</div>
		</aside>
	</div>
</main>
