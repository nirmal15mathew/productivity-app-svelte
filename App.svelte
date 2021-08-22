<script>
  import AppHeader from "./components/AppHeader.svelte";
  import NavBar from "./components/NavBar.svelte";
  import Home from "./pages/Home.svelte";
  import Dash from "./pages/Dash.svelte";
  import Profile from "./pages/Profile.svelte";
  import Add from "./pages/Add.svelte";
  import { HomeIcon, UserIcon, GridIcon, PlusIcon } from "svelte-feather-icons";

  const navBarConf = [
    {
      icon: HomeIcon,
      comp: Home
    },
    {
      icon: GridIcon,
      comp: Dash
    },
    {
      icon: PlusIcon,
      comp: Add
    },
    {
      icon: UserIcon,
      comp: Profile
    }
  ];
  let activeNav = 0;
  function changeNav(ind) {
    activeNav = ind;
  }
</script>
<AppHeader appTitle="App"></AppHeader>
<section>
  <svelte:component this={navBarConf[activeNav].comp}></svelte:component>
</section>
<NavBar 
  navItems={navBarConf} 
  onChangeHandler={changeNav} 
  activeNav={activeNav}
/>
<style>
</style>
