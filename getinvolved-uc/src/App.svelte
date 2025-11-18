<script>
  import EventForm from "./lib/EventForm.svelte";
  import Events from "./lib/Events.svelte";
//import Header from "./lib/Header.svelte";
  import LocationForm from "./lib/LocationForm.svelte";
  import News from "./lib/News.svelte";
  import Orgs from "./lib/Orgs.svelte";
  import Sidebar from "./lib/Sidebar.svelte";
  import eventsdata from "./lib/eventsdata.js";

  import ccat from "../public/logosimgs/communityaction.jpg";
  import aclogo from "../public/logosimgs/ucanimationclub.jpg";


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

  let numAtt;

  let roomSelection = $state("")

  let availableRooms = $state()

  //states for event form
  let eventTitle = $state()
  let eventOrg = $state("studyroom")
  let privateEvent = $state(false)
  let eventCatagory = $state()
  let eventPerks = $state()
  let eventDescription = $state()
  let startDate = $state()
  let startTime = $state()
  let endDate = $state()
  let endTime = $state()

  //schedule json
  let schedule = $state({
    "Langsam 505": [
      {
        date: "Monday",
        start: "12:30PM",
        end: "2:00PM",
        title: "Study",
      },
      {
        date: "Monday",
        start: "3:30PM",
        end: "5:30PM",
        title: "Study",
      },
    ],
    "Langsam 520": [
      {
        date: "Monday",
        start: "3:30PM",
        end: "5:30PM",
        title: "Study",
      },
    ],
    "Langsam 521": [
      {
        date: "Monday",
        start: "3:30PM",
        end: "5:30PM",
        title: "Study",
      },
    ],
    "Langsam 613": [
      {
        date: "Monday",
        start: "3:30PM",
        end: "5:30PM",
        title: "Study",
      },
    ],
    "Old Chem 518": [
      {
        date: "Monday",
        start: "3:30PM",
        end: "5:30PM",
        title: "Study",
      },
    ],
    "Swift 716": [
      {
        date: "Monday",
        start: "3:30PM",
        end: "5:30PM",
        title: "Study",
      },
      {
        date: "Wednesday",
        start: "6:00PM",
        end: "7:00PM",
        title: "Club Meeting",
      },
    ],
    "Swift 516": [
      {
        date: "Monday",
        start: "3:30PM",
        end: "5:30PM",
        title: "Study",
      },
      {
        date: "Tuesday",
        start: "6:30PM",
        end: "8:00PM",
        title: "Club Meeting",
      },
    ],
  })

  const eventId = [2];
  const orgEvents = eventsdata.events.filter(event => eventId.includes(event.id));
</script>

<main>
  <Sidebar bind:selectedButton bind:createEvent />
  <!--<Header />-->

  {#if selectedButton === "home"}
    <div class="view">
      <div class="home-view">
        <div class="my-orgs">
          <h1>My Organizations</h1>
          <div class="orgs-list" style="padding-left: 40px">
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
              <img
                src={ccat}
                class="my-org-logo"
              />
              <div class="align-disp">
                <h2 class="my-org-text">
                 Community Action Team
                </h2>
              </div>
            </div>

            <div class="org">
              <img
                src={aclogo}
                class="my-org-logo"
              />
              <div class="align-disp">
                <h2 class="my-org-text">
                  Animation Club
                </h2>
              </div>
            </div>
          </div>
        </div>

        <div>
          <h1>Events Hosted by My Organizations</h1>

          <div style="display: flex; flex-wrap: wrap; padding-left: 40px">
          {#each orgEvents as event}
            <div style=" padding-top: 20px">
              <div class="event"
              >
                <img src={event.img} style="width: 400px; height: 250px; object-fit: cover; object-position: center;" />
                <div style="height: 60px">
                  <h3 style="padding: 15px">{event.title}</h3>
                </div>

                <p style="padding-left: 15px; padding-bottom: 10px"><i class="bi bi-calendar-event"></i>  {event.date}</p>
                <p style="padding-left: 15px; padding-bottom: 20px"><i class="bi bi-geo-alt-fill"></i>  {event.location}</p>

                <div
                  style="display: flex; padding-top: 10px; padding-bottom: 10px ; background-color: #f3f3f3; align-items: center"
                >
                  <img
                    src={event.logo}
                    style="width: 30px; height: 30px; border-radius: 50%; margin-left: 10px; margin-right: 10px"
                  />
                  <p>{event.org}</p>
                </div>
              </div>
            </div>
          {/each}
        </div>
        </div>

        <div class="news" style="padding-top: 40px;">
          <h1 style="margin-bottom: 20px">Latest News</h1>
          <div> <News /> </div>
        </div>
      </div>
    </div>
  {:else if selectedButton === "events"}
    <div class="view">

      <div class="form-view">

        {#if locationForm}
            <LocationForm bind:locationForm bind:onCampus bind:location {numAtt} bind:roomSelection bind:availableRooms bind:schedule/>
        {:else if createEvent}
          <EventForm bind:locationForm bind:createEvent bind:location bind:numAtt bind:availableRooms bind:startDate bind:startTime bind:endDate bind:endTime bind:eventTitle bind:eventOrg bind:privateEvent bind:eventCatagory bind:eventPerks bind:eventDescription bind:schedule/>
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
      <div style="margin-left: 37%; margin-top: -20px; margin-bottom: 20px">
        <div>
        <label for="search">Search:</label>
        <input id="search" name="search"/>
        </div>
      </div>
      <Orgs />
    </div>
    </div>
  <!-- {:else if selectedButton === "news"}
    <div class="view">
      <div class="news-view">
        <h1>News</h1>


      </div>
      <News />
    </div>-->
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
    .event {
        box-shadow: 0px 0px 2px black;
    }

    .event:hover {
         box-shadow: 0px 0px 5px black;
    }
</style>
