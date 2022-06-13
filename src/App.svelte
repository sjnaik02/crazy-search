<script>
  import SearchBar from "./lib/SearchBar.svelte";
</script>

<div class="wrapper">
<main>
  <h1>Crazy Search!</h1>
  <SearchBar />
  <div class="silly-text">
    <p class="text">The source code for this project can be found on <a href="https://github.com/sjnaik02/crazy-search" target="_blank" rel="noopener noreferrer">GitHub</a></p>
    <p class="text"><a target="_blank" href="https://icons8.com/icon/30453/google-sheets">Google Sheets</a> && <a target="_blank" href="https://icons8.com/icon/100417/google-docs">Google Docs</a> icons by <a target="_blank" href="https://icons8.com">Icons8</a></p>
    <p class="text">Created by <a href="https://twitter.com/sjnaik02" target="_blank" rel="noopener noreferrer">Shourya Naik</a></p>
  </div>
</main>
</div>

<style>
  h1{
    font-size: 64px;
    font-family: 'Roboto Mono', monospace;
  }
  .wrapper{
    box-sizing: border-box;
    font-size: 16px;
    font-family: monospace;
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
  .silly-text{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-top: 30px;
    width: clamp(100vw, 40vw, 600px);
    text-align: center;
  }
  p{
    margin: 5px;
    padding: 0;
    font-size: 1rem;
  }
  .text{
    font-family: monospace;
    color: #999;
  }
  .text a{
    color: #000;
  }
</style>
