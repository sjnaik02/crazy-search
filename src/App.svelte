<script>
  import SearchBar from "./lib/SearchBar.svelte";
</script>

<div class="wrapper">
<main>
  <h1>Hello World</h1>
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
    color: #333;
    background-color: #fff;

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
