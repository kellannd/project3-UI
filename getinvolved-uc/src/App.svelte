<script>
  import EventForm from "./lib/EventForm.svelte";
  import Header from "./lib/Header.svelte";
  import Sidebar from "./lib/Sidebar.svelte";

  let selectedButton = $state("home");

  import acmwlogo from "./assets/acmw.jpg";

  let createEvent = $state(false);
</script>

<main>
  <Sidebar bind:selectedButton bind:createEvent/>
  <Header />

  {#if selectedButton === "home"}
    <div class="view">
      <div class="home-view">
        <div class="my-orgs">
          <h1>My Organizations</h1>
          <div class="orgs-list">
            <div class="org">
              <img
                src={acmwlogo}
                style="height: 80px; margin-top: 10px; margin-left: 10px; padding-right: 10px"
              />
              <div style="display: flex; align-items: center;">
                <h2 style="font-weight: lighter">
                  University of Cincinnati ACM-W Student Chapter
                </h2>
              </div>
            </div>

            <div class="org">
              <h1>acmw</h1>
            </div>
          </div>
        </div>

        <div class="news">
          <h1>Latest News</h1>
        </div>
      </div>
    </div>
  {:else if selectedButton === "events"}
    <div class="view">
      {#if createEvent}
        <div class="view">
          <button
          class="close-btn"
            onclick={() => {
              createEvent = false;
            }}><i class="bi bi-x-lg"></i></button
          ><br />
          <div style="  display: flex; justify-content: center;">
            <EventForm />
          </div>
        </div>
      {:else}
        <h1>events</h1>

        <button
          onclick={() => {
            createEvent = true;
          }}>Create New Event</button
        >
      {/if}
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
  @import "./app.css";

  .view {
    width: calc(100% - 100px);
    height: calc(100% - 80px);
    padding-top: 80px;
    margin-left: 100px;
  }

  .home-view {
    padding-left: 80px;
    padding-top: 50px;
  }

  .my-orgs {
    padding-bottom: 50px;
  }

  .orgs-list {
    display: flex;
  }

  .org {
    /* border-width: 1px;
    border-color: black;
    border-style: solid; */
    box-shadow: 0px 0px 2px black;
    background-color: white;
    width: 400px;
    height: 100px;
    margin-right: 40px;
    display: grid;
    grid-template-columns: 1fr 4fr;
    grid-template-rows: auto;
    font-weight: lighter;
    margin-top: 20px;
  }

  .org:hover {
    box-shadow: 0px 0px 5px black;
  }

  .close-btn {
    background-color: transparent;
    border: none;
        position: absolute;
    right: 0;
    top: 0;
    padding-top: 110px;
    padding-right: 30px;
    font-size: 30px
  }
</style>
