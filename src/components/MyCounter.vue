<template>
	<div>
		<div class="counter">
			<div>Number of {{fruit}}: {{count}}</div>
			<div>Please pay $ {{price}}</div>
			<button @click="increment()">Click</button>
		</div>
	</div>
</template>

<script>
export default {
	props: ['available', 'rate', 'fruit'],
	data() {
		return {
			toggle: true,
			count: 0,
		};
	},
	computed: {
		price() {
			return this.rate * this.count;
		},
		countDisplay() {
			return 'My count is: ' + this.count;
		},
	},
	methods: {
		increment() {
			if (this.available < this.rate) return;
			this.count++;
			this.$emit('update', this.rate);
		},
	},
};
</script>

<style>
.counter {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 20px;
}
</style>


