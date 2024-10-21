<script setup lang="ts">
// JS
// import {menu, cashInRegisteer, orderQueue, addNewPizza, placeOrder, completeOrder} from '../index.js' 

// TS


type Pizza = {
	id: number,
	name: string,
	price: number,
}

type Status = "ordered" | "completed"

type Order = {
	id: number,
	status: Status,
	pizza: Pizza,
}

const menu: Pizza[] = [
	{
		id: 1,
		name: 'Margarita',
		price: 8
	},
	{
		id: 2,
		name: 'Papperoni',
		price: 10
	},
	{
		id: 3,
		name: 'Hiwaiian',
		price: 10
	},
	{
		id: 4,
		name: 'Veggie',
		price: 9
	}
]

let cashInRegisteer: number = 100
let nextOrderId: number = 1
const orderQueue: Order[] = [];

function addNewPizza(pizzaObj: Pizza) {
	menu.push(pizzaObj)
}

function placeOrder(pizzaName: string) {
	const selectedPizza = menu.find(pizzaObj => pizzaObj.name === pizzaName)
	if (selectedPizza === undefined) {
		console.error(`${pizzaName} is not on the menu`)
		return
	}
	cashInRegisteer += selectedPizza.price
	const newOrder: Order = {
		id: nextOrderId++, pizza: selectedPizza, status: "ordered"
	}
	orderQueue.push(newOrder)
	return newOrder
}

function completeOrder(orderId: number) {
	const order = orderQueue.find(order => order.id === orderId)
	if (order === undefined) {
		console.error(`Order ${orderId} not found`)
		return
	}
	order.status = "completed"
	return order
}

// Type Narroving
type Identifier = number | string;

function getPizzaDetail (identifier: Identifier) {
	if(typeof identifier === 'string') {
		return menu.find(pizza => pizza.name.toLowerCase() === identifier.toLowerCase())
	} else {
		return menu.find(pizza => pizza.id === identifier)
	}
}


addNewPizza({ id: 5, name: 'Chicken', price: 12 });
addNewPizza({ id: 6, name: 'BBQ', price: 12 });
addNewPizza({ id: 7, name: 'Spicy', price: 11 });

getPizzaDetail(1);
placeOrder("Chicken");
placeOrder("Papperoni");
completeOrder(1);
placeOrder("Anchovy");
placeOrder("Veggie");
completeOrder(2);

console.log("Menu:", menu);
console.log("Cash in Register:", cashInRegisteer);
console.log("Order Queue:", orderQueue);


// Explicit Types
// let numbersOfWheels: number = 4;
// let isStudent: boolean = true;


//  Custom Types
// type Food = string;
// let favoriteFood: Food = "pizza";

// type Person = {
// 	name: string,
// 	age: number,
// 	isStudent: boolean
// }

// let person: Person = {
// 	name: 'John',
// 	age: 30,
// 	isStudent: true,
// }

// let person2: Person = {
// 	name: 'Mike',
// 	age: 42,
// 	isstudent: true,
// }


//  Nested Object Types
// type Adress = {
// 	street: string,
// 	city: string,
// 	country: string,
// }

// type Person = {
// 	name: string,
// 	age: number,
// 	isStudent: boolean,
// 	adress: Adress
// }


// let person1: Person = {
// 	name: 'John',
// 	age: 30,
// 	isStudent: true,
// 	adress: {
// 		street: '123 Main St',
// 		city: 'New York',
// 		country: 'USA'
// 	}
// }

// let person2: Person = {
// 	name: 'Mike',
// 	age: 42,
// 	isStudent: true,
// 	adress: {
// 		street: '123 Main St',
// 		city: 'New York',
// 		country: 'USA'
// 	}
// }


//  Optional Properties
// type Adress = {
// 	street: string,
// 	city: string,
// 	country: string,
// }

// type Person = {
// 	name: string,
// 	age: number,
// 	isStudent: boolean,
// 	adress?: Adress
// }


// let person1: Person = {
// 	name: 'John',
// 	age: 30,
// 	isStudent: true,
// }

// let person2: Person = {
// 	name: 'Mike',
// 	age: 42,
// 	isStudent: true,
// 	adress: {
// 		street: '123 Main St',
// 		city: 'New York',
// 		country: 'USA'
// 	}
// }


// Array Types
// let prices: number[] = [100, 200, 300];

// type Person = {
// 	name: string,
// 	age: number,
// 	isStudent: boolean,
// }

// let person1: Person = {
// 	name: 'John',
// 	age: 30,
// 	isStudent: true,
// }

// let person2: Person = {
// 	name: 'John',
// 	age: 30,
// 	isStudent: true,
// }

// let person3: Person = {
// 	name: 'John',
// 	age: 30,
// 	isStudent: true,
// }

// let people: Person[] = [person1, person2, person3];
// let people2: Array<Person> = [person1, person2, person3];


// Literal Types
// let myName = "John";
// const myName2 = "John";


// Unions
// type User = {
// 	name: string,
// 	role: "admin" | "user" | "guest",
// }

// type UserRole = User["role"];

// let userRole: UserRole = "admin";
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
	padding-inline: 40px;
	padding-block: 40px;
}
</style>
