<script>
  export let navItems = [];
  export let onChangeHandler;
  export let activeNav;
</script>
<nav>
  <ul>
    {#each navItems as item, i}
      <li 
        class={i === activeNav ? "nav-item active" : "nav-item"} 
        on:click={() => onChangeHandler(i)}
      >
        <svelte:component this={item.icon} props={i === activeNav ? {width: '3px'}: {}}></svelte:component>
      </li>
    {/each}
  </ul>
</nav>
<style>
  nav {
    width: 100vw;
    position: fixed;
    bottom: 0;
    background: #eee;
    box-shadow: 0 0 3px 3px rgba(0, 0, 0, 0.1);
  }
  ul {
    display: flex;
    list-style: none;
    height: 1.3em;
    align-content: center;
    justify-content: space-around;
    padding: 0;
  }
  li {
    color: #283f3b;
  }
  .nav-item {
    border-radius: 0.3em;
    height: 1.4em;
    padding: 0.1em;
    transition: background 0.2s;
    cursor: pointer;
  }
  .nav-item.active {
    color: #3d3b8e;
  }
</style>