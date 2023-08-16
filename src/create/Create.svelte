<script>
    import BackButtonRow from "../common/BackButtonRow.svelte";
    import BookCover from "../common/BookCover.svelte";
    import Button from "../common/Button.svelte";
    import Header from "../common/Header.svelte";
    import { httpPost } from "../common/api.js";

    let title = "";

    function handleInput(evt) {
        title = evt.target.value;
    }

    // reactive statement, always label it with $:, code after the : is rerun whenever variable specified changes
    // $: console.log({title})
  </script>
  
  <style>
    form {
      display: grid;
      grid-auto-rows: auto;
      grid-template-columns: 1fr;
      gap: var(--spacingXLarge);
    }
    .fields {
      display: grid;
      grid-auto-rows: auto;
      gap: var(--spacingMedium);
    }
    .preview {
      display: grid;
      grid-template-columns: minmax(20vw, 10rem);
      grid-template-rows: minmax(32vw, 16rem);
    }
    @media (min-width: 48rem) {
      form {
        grid-template-columns: 60vw 20vw;
      }
    }
  </style>
  
  <BackButtonRow />
  
  <Header element="h1" size="large">Create</Header>
  
  <form>
    <div class="fields">
        <label>
            <span>Title</span>
            <input type="text" on:input={handleInput} value={title}/>
        </label>
    </div>
  
    <div>
      <Header>Preview</Header>
      <div class="preview">
      </div>
    </div>
  </form>