<script>
  import EventForm from "./lib/EventForm.svelte";
  import Events from "./lib/Events.svelte";
  import Header from "./lib/Header.svelte";
  import LocationForm from "./lib/LocationForm.svelte";
  import News from "./lib/News.svelte";
  import Orgs from "./lib/Orgs.svelte";
  import Sidebar from "./lib/Sidebar.svelte";

  let selectedButton = $state("home");

  import acmwlogo from "./assets/acmw.jpg";

  let createEvent = $state(false);

  let locationForm = $state(false);

  let onCampus = $state("oncampus")

  let location = $state({
    title: "",
    address: "",
    city: ""
  })
</script>

<main>
  <Sidebar bind:selectedButton bind:createEvent />
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
                class="my-org-logo"
              />
              <div class="align-disp">
                <h2 class="my-org-text">
                  University of Cincinnati ACM-W Student Chapter
                </h2>
              </div>
            </div>

            <div class="org">
              <h1>acmw</h1>
            </div>
          </div>
        </div>

        <div>
          <h1>Events Hosted by My Organizations</h1>

          <div class="orgs-events-list">

          </div>
        </div>

        <div class="news">
          <h1>Latest News</h1>
        </div>
      </div>
    </div>
  {:else if selectedButton === "events"}
    <div class="view">

      <div class="form-view">

        {#if locationForm}
            <LocationForm bind:locationForm bind:onCampus bind:location/>
        {:else if createEvent}
          <EventForm bind:locationForm bind:createEvent bind:location />
        {:else}
        <button
          class="create-event-btn"
            onclick={() => {
              createEvent = true;
            }}>Create New Event</button
          ><br>
        <h1 style="margin-top: -20px">Events</h1>
          <div>
            <Events />
          </div>
        {/if}
    </div>
    </div>
  {:else if selectedButton === "orgs"}
    <div class="view">
      <div>
      <h1 class="org-title">Organizations</h1>
      <Orgs />
    </div>
    </div>
  {:else if selectedButton === "news"}
    <div class="view">
      <div class="news-view">
        <h1>News</h1>


      </div>
      <News />
    </div>
  {:else}
    <div class="view">
      <div class="links-view">
      <h1>Forms and Links</h1>

      <h2 class="forms-and-links-text">This page would contain the same links and forms as the original GetInvolved UI.</h2>
    </div>
    </div>
  {/if}
</main>

<style>
  @import "./app.css";
</style>
