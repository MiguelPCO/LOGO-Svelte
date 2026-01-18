<script lang="ts">
    type Product ={
        id: number;
        name: string;
        price: number;
    }

    const PRODUCTS: Product[] = [
        {id: 1, name: 'manzana', price: 1},
        {id: 2, name: 'pera', price: 1.5},
        {id: 3, name: 'uva', price: 2.5},
        {id: 4, name: 'sandía', price: 6},
        {id: 5, name: 'kiwi', price: 3.8},
    ]
</script>
<main class="container mx-auto p-4">
	<h1 class="text-2xl font-bold mb-6">Frutería LOGO</h1>

	<section class="mb-8">
		<h2 class="text-xl font-semibold mb-4">Productos Disponibles</h2>
		<div class="flex gap-3 flex-wrap">
			{#each PRODUCTS as product}
				<button 
					class="px-4 py-2 bg-green-600 text-white rounded-lg hover:bg-green-700 transition"
				>
					{product.name} - {product.price.toFixed(2)}€
				</button>
			{/each}
		</div>
	</section>

</main>
