<script>
  import SearchBar from "./lib/SearchBar.svelte";
</script>

<div class="wrapper">
<main>
  <h1>Crazy Search!</h1>
  <SearchBar />
</main>
</div>

<style>
  .wrapper{
    box-sizing: border-box;
    font-size: 16px;
    font-family: sans-serif;
    line-height: 1.5;
    margin: 0;
    padding: 0;
    background-color: #15133C;
    color: #fff;

  }
  main{
    width: 100vw;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
</style>
