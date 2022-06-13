<script>
  let search = "";
  let defaultSearchEngine = "google";
  let searchEngine = "";
  const engines = ["YouTube", "Docs", "Drive", "Sheets", "GitHub", "Google"];

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


<div class="wrapper">
  <img src={`/${searchEngine ? searchEngine : defaultSearchEngine}.svg`} alt="search term icon" class="icon">
  <input bind:value={search} on:keydown={handleKeyDown}>
  <button on:click={handleClick}><img src="/angles-right.svg" alt="Right arrows"></button>
</div>
<span>
{#if autocomplete(search)&&searchEngine === ""}
   Press right arrow to search with {autocomplete(search)}
{/if}
</span>
  
<style>
  .icon{
    border: 1px solid #000;
    border-radius: 50%;
    padding: 5px;
    width: 45px;
    height: 45px;
    margin: 30px;
    box-shadow:  12px 12px 24px #d8d8d8,
                -12px -12px 24px #ffffff;
  }
  span{
    height: 1rem;
    font-family: monospace;
    margin-top: 10px;
    margin-bottom: 30px;
    font-size: 1.2rem;
  }
  input{
    border: 1px solid black;
    padding: 20px;
    font-size: 1.2rem;
    width : clamp(250px, 40vw, 600px);
    border-radius: 50px;
    background-color: #fff;
    box-shadow:  25px 25px 50px #d9d9d9,
                -25px -25px 50px #ffffff;
    font-family: monospace;
  }
  input:focus{
    box-shadow: inset 8px 8px 6px #e6e6e6,
                inset -12px -12px 30px #ffffff;
    outline: none;
  }
  button{
    height: 60px;
    width: 60px;
    margin: 30px;
    padding: 10px;
    border-radius: 100%;
    background-color: #fff;
    font-size: 1.3rem;
    box-shadow:  12px 12px 24px #d8d8d8,
                -12px -12px 24px #ffffff;
  }
  button:active{
    box-shadow: inset 12px 12px 24px #d8d8d8,
                inset -12px -12px 24px #ffffff;
    outline: none;
  }
  .wrapper{
    display: flex;
    align-items: center;
    justify-content: center;
  }
</style>