<script>
  export let appTitle = "";
  export let appIcon;
</script>
<header>
  <figure>
    <img src={appIcon} alt="">
    <h1>{appTitle}</h1>
  </figure>
</header>
<style>
  figure,
  header,
  h1 {
    margin: 0;
    color: #333;
    width: min-content;
  }
  header {
    display: flex;
    align-items: center;
    padding: 0.6em;
  }
  h1 {
    font-size: 1.4rem;
    font-weight: 500;
  }
  figure {
    display: flex;
  }
</style>