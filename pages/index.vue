<script setup lang="ts">

// !! JS

// const menu = [
// 	{
// 		name: 'Margarita',
// 		price: 8
// 	},
// 	{
// 		name: 'Papperoni',
// 		price: 10
// 	},
// 	{
// 		name: 'Hiwaiian',
// 		price: 10
// 	},
// 	{
// 		name: 'Veggie',
// 		price: 9
// 	}
// ]

// const cashInRegisteer = 100
// const orderQueue = [];
// const nextOrderId = 1

// function addNewPizza(pizzaObj: any) {
// 	menu.push(pizzaObj)
// }

// function placeOrder(pizzaName: any) {
// 	const selectedPizza = menu.find(pizzaObj => pizzaObj.name === pizzaName)
// 	cashInRegisteer += selectedPizza.price
// 	const newOrder = {
// 		id: nextOrderId++,
// 		pizza: selectedPizza,
// 		status: "ordered"
// 	}
// 	orderQueue.push(newOrder)
// 	return newOrder
// }

// function completeOrder(orderId: number) {
// 	const order = orderQueue.find(order => order.id === orderId)
// 	order.status = "completed"
// 	return order
// }

// addNewPizza({name: 'Chicken',price: 12});
// addNewPizza({name: 'BBQ',price: 12});
// addNewPizza({name: 'Spicy',price: 11});

// placeOrder("Chicken");

// completeOrder(1);

// console.log(menu, cashInRegisteer, orderQueue)


// !! TS

const menu = [
	{
		name: 'Margarita',
		price: 8
	},
	{
		name: 'Papperoni',
		price: 10
	},
	{
		name: 'Hiwaiian',
		price: 10
	},
	{
		name: 'Veggie',
		price: 9
	}
]

const cashInRegisteer = 100
const orderQueue = [];
const nextOrderId = 1

function addNewPizza(pizzaObj) {
	menu.push(pizzaObj)
}

function placeOrder(pizzaName) {
	const selectedPizza = menu.find(pizzaObj => pizzaObj.name === pizzaName)
	cashInRegisteer += selectedPizza.price
	const newOrder = {
		id: nextOrderId++, pizza: selectedPizza, status: "ordered"
	}
	orderQueue.push(newOrder)
	return newOrder
}

function completeOrder(orderId: number) {
	const order = orderQueue.find(order => order.id === orderId)
	order.status = "completed"
	return order
}

addNewPizza({ name: 'Chicken', price: 12 });
addNewPizza({ name: 'BBQ', price: 12 });
addNewPizza({ name: 'Spicy', price: 11 });

placeOrder("Chicken");

completeOrder(1);

console.log(menu, cashInRegisteer, orderQueue)


</script>

<template>
	<main>
		<div class="container">
			<h1>TypeScript Cource</h1>
			<div>{{ menu }}</div>
			<div>{{ cashInRegisteer }}</div>
			<div>{{ orderQueue }}</div>
		</div>
	</main>
</template>

<style scoped>
.container {
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	gap: 30px;
}
</style>
