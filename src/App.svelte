<script>
  import SearchBar from "./lib/SearchBar.svelte";
</script>

<div class="wrapper">
<main>
  <h1>Crazy Search!</h1>
  <SearchBar />
  <p class="text"><a target="_blank" href="https://icons8.com/icon/30453/google-sheets">Google Sheets</a> && <a target="_blank" href="https://icons8.com/icon/100417/google-docs">Google Docs</a> icon by <a target="_blank" href="https://icons8.com">Icons8</a></p>
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
    background-color: #fff;
    color: #000;

  }
  main{
    width: 100vw;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .text{
    font-family: monospace;
    color: #999;
    margin-bottom: 50px;
  }
  .text a{
    color: #000;
  }
</style>
