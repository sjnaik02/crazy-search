<script>
  let search = "";
  let defaultSearchEngine = "google";
  let searchEngine = "";
  //google, youtube, github, drive, docs and sheets
  const array = ["YouTube", "Drive", "Google"];

  const autocomplete = (search) => {
    let autocomplete = '';
    let firstWord = search.split(' ')[0];
    array.forEach(element => {
      if (element.substring(0, firstWord.length>0?firstWord.length:1).toUpperCase() === firstWord.toUpperCase()) {
        autocomplete = element;
      }
    });
    return autocomplete;
  };  

  const handleKeyDown = (e) => {
    if(autocomplete(search) !== "" && e.key === "ArrowRight"){
      searchEngine = autocomplete(search);
      search = "";
    } else if (search === "" && e.key === "Backspace"){
      searchEngine = "";
    }
  };

  const handleClick = () =>{
    if(searchEngine === ""){
      window.open(`https://${defaultSearchEngine}.com/search?q=${search}`, '_blank');
    }
  };

</script>

<input bind:value={search} on:keydown={handleKeyDown}>
<button on:click={handleClick}>Search!</button>
<span>
{#if autocomplete(search)}
   Press right arrow to search with {autocomplete(search)}
{/if}
<p>{searchEngine}</p>
</span>

<style>
  span{
    height: 1rem;
  }
  input{
    padding: 10px;
    width : clamp(300px, 30vw, 600px);
    border-radius: 50px;
    background-color: #cacaca;
  }
  button{
    margin: 20px;
    padding: 10px;
    border-radius: 10px;
    background-color: #cacaca;
  }
</style>