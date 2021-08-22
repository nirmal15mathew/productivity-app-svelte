<script>
	import TodoItem from "./TodoItem.svelte";
	export let todoList = [];
	export let eventHandler;
</script>
<ul>
	{#each todoList as todo, ind}
		<li>
			<TodoItem 
								todoTitle={todo.title} 
								todoState={todo.state}
								todoEventHandle={eventHandler}
								index={ind}
								>
			</TodoItem>
		</li>
	{/each}
</ul>
<style>
		ul {
		  list-style: none;
		  padding: 0;
		  transition: height 200ms;
		}
</style>