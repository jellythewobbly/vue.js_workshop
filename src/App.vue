<template>
  <div id="app">
		<my-counter v-for="item in items" :key="item.label"
			:rate="item.price"
			:available="available"
			:fruit="item.label"
			@update="updateAvailable"></my-counter>
  </div>
</template>

<script>
import MyCounter from './components/MyCounter.vue';

export default {
	name: 'app',
	components: {
		MyCounter,
	},
	data() {
		return {
			available: 100,
			count: 0,
			items: [
				{ label: 'Apples', price: 5 },
				{ label: 'Bananas', price: 10 },
				{ label: 'Coconuts', price: 20 },
			],
		};
	},
	methods: {
		updateAvailable(value) {
			this.available -= value;
		},
		fetchItems() {
			setTimeout(() => {
				this.items = [
					{ label: 'Apples', price: 5 },
					{ label: 'Bananas', price: 10 },
					{ label: 'Coconuts', price: 20 },
				];
			}, 1000);
		},
	},
	created() {
		window.vm = this;
		this.fetchItems();
	},
	mounted() {},
};
</script>

<style>
#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}
</style>
