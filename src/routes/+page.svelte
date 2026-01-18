<script lang="ts">
    type Product ={
        id: number;
        name: string;
        price: number;
    }

    type CartItem = {
		id: number;
		productId: number;
		name: string;
		price: number;
	}

    const PRODUCTS: Product[] = [
        {id: 1, name: 'manzana', price: 1},
        {id: 2, name: 'pera', price: 1.5},
        {id: 3, name: 'uva', price: 2.5},
        {id: 4, name: 'sandía', price: 6},
        {id: 5, name: 'kiwi', price: 3.8},
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
</script>
<main class="container mx-auto p-4">
	<h1 class="text-2xl font-bold mb-6">Frutería</h1>

	<section class="mb-8">
		<h2 class="text-xl font-semibold mb-4">Productos Disponibles</h2>
		<div class="flex gap-3 flex-wrap">
			{#each PRODUCTS as product}
				<button 
					class="px-4 py-2 bg-green-600 text-white rounded-lg hover:bg-green-700 transition"
					on:click={() => addToCart(product)}
				>
					{product.name} - {product.price.toFixed(2)}€
				</button>
			{/each}
		</div>
	</section>

    <section>
		<h2 class="text-xl font-semibold mb-4">Ticket</h2>
		{#if cart.length === 0}
			<p class="text-gray-500">El carrito está vacío</p>
		{:else}
			<ul class="space-y-2">
				{#each cart as item (item.id)}
					<li class="flex justify-between items-center p-3 bg-gray-50 rounded-lg border">
						<span class="font-medium">
							{item.name} - €{item.price.toFixed(2)}
						</span>
					</li>
				{/each}
			</ul>
            <div class="pt-4 border-t-2 border-gray-300">
				<p class="text-2xl font-bold">
					Total: €{total.toFixed(2)}
				</p>
			</div>
		{/if}
	</section>
</main>
