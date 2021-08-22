<script>
	import { XIcon } from "svelte-feather-icons";
	export let todoTitle = "";
	export let todoState = false;
	export let todoEventHandle;
	export let index;

	function checkboxCheck() {
	  todoEventHandle({
	    type: "toggle-todo",
	    payload: {
	      index
	    }
	  });
	}

	function deleteTodo() {
	  console.log("deleted");
	  todoEventHandle({
	    type: "remove-todo",
	    payload: {
	      index
	    }
	  });
	}
</script>
<div>
	<section class="icon-container" on:click={deleteTodo}>
		<XIcon size="16"></XIcon>
	</section>
	<main class="todo-title"  on:click={checkboxCheck}>
		{todoTitle}
	</main>
	<section class="todo-checkbox"  on:click={checkboxCheck}>
		<input type="checkbox" checked={todoState}>
	</section>
</div>
<style>
	div {
	  display: grid;
	  grid-template-columns: 2em auto 4em;
	  grid-template-rows: 1fr;
	  gap: 0px 0px;
	  grid-auto-flow: row;
	  grid-template-areas: ". . .";
	  padding: 0.5em 0em;
	  border-radius: 0.3em;
	  cursor: pointer;
	  animation: grow 0.2s;
	}
	div:hover {
	  background: rgba(0, 0, 0, 0.1);
	}
	section {
	  display: flex;
	  align-items: center;
	  justify-content: center;
	  color: #333;
	}
	@keyframes grow {
	  from {
	    transform: scale(0);
	  }
	  to {
	    transform: scale(1);
	  }
	}
</style>