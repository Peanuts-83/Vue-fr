<script>
export default {
	name: "MenuItem",
	props: ["addToShoppingCart", "image", "inStock", "name", "price", "quantity"],
	computed: {
		generatePrices() {
			if (this.onSale) {
				console.log('+10%');
				return (this.price * 1.1).toFixed(2);
			} else {
				console.log('-10%');
				return (this.price * 0.9).toFixed(2);
			}
		}
	},
	beforeMount() {
		const date = new Date().getDate();
		if (date % 2 === 0) {
			this.onSale = true;
		}
	},
}
</script>

<template>
	<div class="menu-item">
		<img class="menu-item__image" :src="image.source" :alt="image.alt" />
		<div>
			<span style="color: lightgrey">Prix de référence: {{ price }}</span>
			<h3>{{ name }}</h3>
			<p>Prix : {{ generatePrices }}</p>
			<p v-if="inStock">En stock</p>
			<p v-else>En rupture de stock</p>
			<div>
				<label for="add-item-quantity">Quantité : {{ quantity }}</label>
				<input v-model.number="quantity" id="add-item-quantity" type="number" />
				<button @click="addToShoppingCart(quantity)">
					Ajouter au panier
				</button>
			</div>
		</div>
	</div>
</template>

<style></style>
