<script>
import { each } from "svelte/internal";
import autoAnimate from "@formkit/auto-animate"
import { toast } from '@zerodevx/svelte-toast'
import { nanoid } from "nanoid";


	let todos = [
		{ title: "Bisiklete Çık", id: nanoid(), complete: false},
		{ title: "Oyun Oyna",  id: nanoid(), complete: true},
		{ title: "İlaçlarını Al",  id: nanoid(), complete: true}
	];

	let title2 = "";

	const addTodo = (title) => {
		todos = [ ...todos,
			{ title: title2 , id: nanoid(), num: todos.length + 1, complete: false } ];
	};

	const deleteTodo = (id) => {
		todos = todos.filter(todo => todo.id !== id);
	};

	const completeTodo = (id) => {
		todos = todos.map(todo => {
			if (todo.id === id) {
				todo.complete = !todo.complete;
			}
			return todo;
		});
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
		text-decoration-thickness: 2px;  
	}
</style>


<div class="flex space-y-5 flex-col sm:p-0 p-3 min-h-screen items-center justify-center">
	<div class="flex outline-none focus:outline-none ease-linear transition-all duration-150 sm:flex-row items-center flex-col items-center outline-none focus:outline-none ease-linear transition-all duration-150">
		<input type="text" name="" class="sm:w-80 w-72 mr-1 mb-1 px-3 py-2 cursor-pointer shadow-xl bg-white border-2 rounded text-black text-font" placeholder="Görev Ekle" id="s"  bind:value={title2}>
		<button on:click={addTodo} class="w-20 mr-1 mb-1 px-4 py-2 bg-white rounded text-black ursor-pointer shadow-xl border-2 text-font" id="add"><i class="fa-solid fa-plus"></i></button>
	    {#if todos.length > 0}
		<button on:click={() => {
			todos = todos.filter(todo => !todo);
		}} class="w-20 mr-1 mb-1 px-4 py-2 bg-white rounded text-black ursor-pointer shadow-xl border-2 text-font" id="remove"><i class="fa-solid fa-trash"></i></button>
		{/if}
		{#if todos.length > 0}
		<button on:click={() => {
			todos = todos.map(todo => {
				todo.complete = !todo.complete;
				return todo;
			});
		}} class="w-20 mr-1 mb-1 px-4 py-2 bg-white rounded text-black ursor-pointer shadow-xl border-2 text-font" id="complete"><i class="fa-solid fa-check"></i></button>
		{/if}
	</div>
	
	<div use:autoAnimate class="outline-none focus:outline-none  grid sm:grid-rows-2 sm:grid-cols-2 lg:grid-rows-3 lg:grid-cols-3 grid-cols-1 ease-linear transition-all duration-150 gap-3">
		{#each todos as {id, title, num, complete}, index}
		<div class="flex outline-none focus:outline-none ease-linear transition-all duration-150 px-4 py-2 bg-white cursor-pointer shadow-xl mr-1 mb-1 items-center justify-between rounded sm:w-80 w-72">
			<button  on:click={ () => completeTodo(id)} class="mr-1 mb-1 px-4 py-1 hover:outline hover:outline-offset-2 hover:outline-green-500 bg-green-500 rounded cursor-pointer shadow-xl text-font text-white outline-none focus:outline-none ease-linear transition-all duration-150"><i class="fa-duotone fa-check"></i></button>
			<span class="text-font text-black outline-none focus:outline-none ease-linear transition-all duration-150" class:complete={complete}> {title}</span>
			<button on:click={ () => deleteTodo(id)} class="mt-0.5 rounded text-font text-red-500 text-xl  px-4 py-2"><i class="fa-solid fa-xmark"></i></button>
		</div>
		{/each} 	
	</div>	
	{#if todos.length === 0}
	<div class="flex text-center items-center justify-center">
		<span class="text-font text-black text-xl">Görevleriniz yok</span> 
	</div>	
	{/if}
		<div class="fixed inset-x-0 flex justify-center p-2 bottom-0 w-full">
			<h1 class="text-font text-sm">Bu site github üzerinden açık kaynaklıdır.</h1>
		</div>
		<a href="https://github.com/xDarkShiny/to-do-r" class="fixed top-0 right-5 text-3xl p-2"><i class="fa-brands fa-github"></i></a>
</div>

	
