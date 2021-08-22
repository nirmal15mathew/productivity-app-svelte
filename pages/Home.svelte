<script>
	import TodoBox from "../components/todo-component/TodoBox.svelte";
	let todoList = [
	  {
	    title: "Clear trash",
	    state: true,
	    icon: ""
	  },
	  {
	    title: "Water Plants",
	    state: false,
	    icon: ""
	  }
	];
</script>
<main>
<TodoBox boxTitle="Daily" {todoList}/>
</main>

<style>
  main {
    padding: 1em;
  }
</style>