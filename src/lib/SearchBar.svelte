<script>
  let search = "";
  let defaultSearchEngine = "google";
  //google, youtube, github, drive, docs and sheets
  const array = ["YouTube", "Drive", "google"];

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

  $:if(autocomplete(search)) {
    console.log(autocomplete(search));
  }
</script>

<input bind:value={search}>
<span>
{#if autocomplete(search)}
   Press Tab to search with {autocomplete(search)}
{/if}
</span>

<style>
  span{
    height: 2rem;
  }
  input{
    padding: 10px;
    width : clamp(300px, 30vw, 600px);
  }
</style>