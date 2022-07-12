<script>
import { each } from "svelte/internal";
import autoAnimate from "@formkit/auto-animate"


	let todos = [
		{ name: "Bisiklete Çık", id: "1", complete: false},
		{ name: "Valo Oyna Ark Sat", id: "2", complete: true},
		{ name: "İlaçlarını Al", id: "3", complete: true}
	];
	let name2 = "";
	

	const addTodo = () => {
		let todo = {
		name: name2,
		id: todos.length + 1,
		complete: false
	};
		todos = [...todos, todo];
		name2 = ""
		
	};

	const todoComplete = (index) => { 
		const todoComplete2=(index)=>E
		let deleteItem=todos[index];
		console.log(deleteItem)
		let newTodos=todos.filter((item)=>item!=deleteItem);
		todos=newTodos;
	};

	const todoDelete = (index) => { 
		const todoDelete2=(index)=>E
		let deleteItem=todos[index];
		console.log(deleteItem)
		let newTodos=todos.filter((item)=>item!=deleteItem);
		todos=newTodos;
	};

</script>
<style>
	.text-font {
		font-family: 'Inter', sans-serif;
	}
	input::placeholder
	{
		color: rgb(0, 0, 0);
	}
	.complete {
		text-decoration: line-through;
	}
</style>


<div class="flex space-y-5 flex-col sm:p-0 p-3 min-h-screen items-center justify-center">
	<div class="flex sm:flex-row flex-col items-center outline-none focus:outline-none ease-linear transition-all duration-150">
		<input type="text" name="" class="sm:w-80 w-72 mr-1 mb-1 px-3 py-2 cursor-pointer shadow-xl bg-white border-2 rounded text-black text-font" placeholder="Görev Ekle" id="s" bind:value={name2}>
		<button on:click={addTodo} class="w-20 mr-1 mb-1 px-4 py-2 bg-white rounded text-black ursor-pointer shadow-xl border-2 text-font" id="add"><i class="fa-solid fa-plus"></i></button>
	</div>
	
	<div use:autoAnimate class="outline-none focus:outline-none  grid grid-rows-5 ease-linear transition-all duration-150 space-y-2">
		{#each todos as {id, name, complete}, index}
		<div class="flex outline-none focus:outline-none ease-linear transition-all duration-150 px-4 py-2 bg-white cursor-pointer shadow-xl mr-1 mb-1 items-center justify-between rounded sm:w-80 w-72">
			<button on:click={ () => todoComplete(index)} class="mr-1 mb-1 px-4 py-1 hover:outline hover:outline-offset-2 hover:outline-green-500 bg-green-500 rounded cursor-pointer shadow-xl text-font text-white outline-none focus:outline-none ease-linear transition-all duration-150"><i class="fa-duotone fa-check"></i></button>
			<span class="text-font text-black" class:complete={complete}>{index + 1} - {name}</span>
			<button on:click={ () => todoComplete(index)} class="mr-1 rounded text-font text-red-500 mb-1 px-4 py-2"><i class="fa-solid fa-xmark"></i></button>
		</div>
		{/each} 	
	</div>	
	
</div>

	
