<template>
	<main>
		<!--<listItem
		     v-for="(item, index) in database" :name="item.name" :department="item.deparment" :salary="item.salary" :position="index"
             v-on:deleteItem="deleteItem"
		/>-->

		<div>
			<input type="text" v-model="fatherName" placeholder="father name">
			{{fatherName}}
		</div>
		<div class="mt-2">
			<input type="text" v-model="childName" placeholder="child name">
		</div>
	</main>
</template>

<script setup>
import { ref, watch, watchEffect } from "vue";
import listItem from "./components/listItem.vue";

const fatherName = ref('')
const childName = ref('')

//watch([fatherName, childName], ([newValue, oldValue]) =>{
//	console.log(newValue, oldValue)
//})

watchEffect(() => {
	fatherName.value = fatherName.value + "="
})

let database = ref([
	{
		name: "Johnny",
		deparment: "Marketing",
		salary: 30000
	},
	{
		name: "Sarah",
		deparment: "Engineering",
		salary: 72000
	},
	{
		name: "Terrance",
		deparment: "Executive",
		salary: 125000
	}
]);

function deleteItem(position) {
	database.value.splice(position, 1);
}

console.log(database.value)

</script>


<style scoped>
main {
	display: flex;
	justify-content: center;
	flex-direction: column;
}
.mt-2{
	margin-top: 10px;
}
</style>
