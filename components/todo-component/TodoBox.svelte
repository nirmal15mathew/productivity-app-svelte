<script>
	import TodoList from "./TodoList.svelte";
	import { onMount } from "svelte";
	export let boxTitle = "";
	export let todoList = [];
	let currentList = [...todoList];
	function eventHandler(action) {
	  switch (action.type) {
	    case "toggle-todo":
	      currentList[action.payload.index].state = !currentList[
	        action.payload.index
	      ].state;
	      break;
	    case "add-todo":
	      let newTodo = {
	        title: action.payload.title,
	        state: false,
	        icon: ""
	      };
	      currentList = [...currentList, newTodo];
	      break;
	    case "remove-todo":
	      currentList.splice(action.payload.index, 1);
	      currentList = currentList;
	      break;
	    default:
	      console.log("Specify Please");
	      break;
	  }
	}
	onMount(() => {
	  document.querySelector(".input-box").addEventListener("keypress", keyPress);
	});
	function keyPress(e) {
	  if (e.key === "Enter") {
	    eventHandler({
	      type: "add-todo",
	      payload: {
	        title: e.target.value
	      }
	    });
	    e.target.value = "";
	  }
	}
</script>
<div>
	<header>
		<h3 contenteditable="true">
			{boxTitle}
		</h3>
	</header>
	<section>
		<TodoList todoList={currentList} {eventHandler}></TodoList>
	</section>
	<footer>
		<input type="text" placeholder="Enter new todo" class="input-box">
	</footer>
</div>
<style>
	div {
	  padding: 0.9em;
	  box-shadow: 0 0 3px 3px rgba(0, 0, 0, 0.1);
	  border-radius: 0.3em;
	}
	header {
	  display: flex;
	  width: 100%;
	  align-items: center;
	  justify-content: center;
	}
	footer,
	input {
	  width: 95%;
	}
	input {
	  border: 0;
	  border-radius: 0.3em;
	  background-color: rgba(0, 0, 0, 0.1);
	  outline: 0;
	  padding: 0.8em;
	}
	input:focus {
	  background: #eee;
	  box-shadow: 0 0 3px 3px rgba(0, 0, 0, 0.1);
	}
</style>