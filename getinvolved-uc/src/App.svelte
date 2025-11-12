<script>
  import Header from "./lib/Header.svelte";
  import Sidebar from "./lib/Sidebar.svelte";

  let selectedButton = $state("home")

  // export function changeView(view){
  //   selectedButton = view
  // }
</script>

<main>
  <Sidebar bind:selectedButton/>
  <Header />


  {#if selectedButton === "home"}
  <div class="view">
    <h1>home</h1>
  </div>

  {:else if selectedButton === "orgs"}
  <div class="view">
    <h1>Orgs</h1>
  </div>

  {:else if selectedButton === "news"}
  <div class="view">
    <h1>news</h1>
  </div>

  {:else}
  <div class="view">
    <h1>forms</h1>
  </div>

  {/if}
</main>

<style>
  @import './app.css';

  .view{
    width: calc(100% - 100px);
    height: calc(100% - 80px);
    padding-top: 80px;
    margin-left: 100px;
  }
</style>
