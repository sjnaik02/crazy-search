<script>
  let search = "";
  let defaultSearchEngine = "google";
  let searchEngine = "";
  //google, youtube, github, drive, docs and sheets
  const engines = ["YouTube", "Drive", "Google", "Docs", "Sheets", "GitHub"];

  const searchEngines = {
    Google : "https://www.google.com/search?q=",
    YouTube: "https://www.youtube.com/results?search_query=",
    GitHub: "https://github.com/search?q=",
    Drive: "https://drive.google.com/drive/search?q=",
    Docs: "https://docs.google.com/document/u/0/?q=",
    Sheets: "https://docs.google.com/spreadsheets/u/0/?q=",
  }
  
  const autocomplete = (search) => {
    let autocomplete = '';
    let firstWord = search.split(' ')[0];
    engines.forEach(element => {
      if (element.substring(0, firstWord.length>0?firstWord.length:1).toUpperCase() === firstWord.toUpperCase()) {
        autocomplete = element;
      }
    });
    return autocomplete;
  };  

  const removeMessageFromSearch = (s) => {
    return s.substring(s.indexOf('|')+1, s.length);
  }
  
  const handleKeyDown = (e) => {
    if(autocomplete(search) !== "" && e.key === "ArrowRight"){
      searchEngine = autocomplete(search);
      search = `Search ${searchEngine} | `;
    } else if ((search === "" || removeMessageFromSearch(search) == " ")&& e.key === "Backspace"){
      searchEngine = "";
      search = "";
    } else if (e.key === "Enter"){
      handleClick();
    }
  };

  const handleClick = () =>{
    if(searchEngine === ""){
      window.open(`https://${defaultSearchEngine}.com/search?q=${search}`, '_blank');
    } else {
      window.open(`${searchEngines[searchEngine]}${removeMessageFromSearch(search)}`, '_blank');
    }
  };

</script>

<input bind:value={search} on:keydown={handleKeyDown}>
<button on:click={handleClick}>Search!</button>
<span>
{#if autocomplete(search)&&searchEngine === ""}
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
    font-size: 1.5rem;
    width : clamp(300px, 40vw, 600px);
    border-radius: 50px;
    background-color: #cacaca;
  }
  button{
    margin: 20px;
    padding: 10px;
    border-radius: 10px;
    background-color: #cacaca;
    font-size: 1.3rem;
    width: 10rem;
  }
</style>