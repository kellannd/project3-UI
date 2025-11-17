<script>
  import Sidebar from "./lib/Sidebar.svelte";
  import EventForm from "./lib/EventForm.svelte";
  import Events from "./lib/Events.svelte";
  import LocationForm from "./lib/LocationForm.svelte";
  import News from "./lib/News.svelte";
  import Orgs from "./lib/Orgs.svelte";
  import odata from "./data/orgs.json";
  import eventsdata from "./lib/eventsdata.js";
  import acmwlogo from "./assets/acmw.png";
  import acmw from "./assets/acmw.png";

  const imageMap = { "acmw.png": acmw };

  let selectedButton = "home";
  let createEvent = false;
  let locationForm = false;
  let onCampus = "oncampus";
  let location = { title: "", address: "", city: "" };
  let numAtt;
  let roomSelection = "";
  let availableRooms;
  let eventTitle,
    eventOrg = "studyroom",
    privateEvent = false,
    eventCategory,
    eventPerks,
    eventDescription;
  let startDate,
    startTime,
    endDate,
    endTime;
  let schedule = {
    "Langsam 505": [{ date: "Monday", start: "12:30PM", end: "2:00PM", title: "Study" }],
    "Swift 716": [
      { date: "Monday", start: "3:30PM", end: "5:30PM", title: "Study" },
      { date: "Wednesday", start: "6:00PM", end: "7:00PM", title: "Club Meeting" }
    ]
  };

  let selectedOrg = null;
  const orgs = odata[0].organizations;
  let search = "";
  let selectedCategory = [];
  const categories = ["Select All", ...new Set(orgs.map(org => org.category))];

  function openOrg(org) { selectedOrg = org; }
  function closeOrg() { selectedOrg = null; }

  $: filteredOrgs = orgs.filter(org => {
    const matchesSearch = org.name.toLowerCase().includes(search.toLowerCase());
    const matchesCategory = selectedCategory.length === 0 || selectedCategory.includes(org.category) || selectedCategory.includes("Select All");
    return matchesSearch && matchesCategory;
  });

  function toggleCategory(cat) {
    if (cat === "Select All") selectedCategory = categories.filter(c => c !== "Select All");
  }

  const eventId = [2];
  const orgEvents = eventsdata.events.filter(event => eventId.includes(event.id));
</script>

<main>
  <Sidebar bind:selectedButton bind:createEvent />

  {#if selectedButton === "home"}
    <div class="view">
      <div class="home-view">
        <div class="my-orgs">
          <h1>My Organizations</h1>
          <div class="orgs-list">
            <div class="org">
              <img src={acmwlogo} class="my-org-logo" />
              <div class="align-disp">
                <h2 class="my-org-text">University of Cincinnati ACM-W Student Chapter</h2>
              </div>
            </div>
          </div>
        </div>

        <div>
          <h1>Events Hosted by My Organizations</h1>
          <div style="display:flex;flex-wrap:wrap">
            {#each orgEvents as event}
              <div style="padding-top:20px">
                <div class="event">
                  <img src={event.img} style="width:400px;height:250px;object-fit:cover;object-position:center"/>
                  <div style="height:60px">
                    <h3 style="padding:15px">{event.title}</h3>
                  </div>
                  <p style="padding-left:15px;padding-bottom:10px"><i class="bi bi-calendar-event"></i> {event.date}</p>
                  <p style="padding-left:15px;padding-bottom:20px"><i class="bi bi-geo-alt-fill"></i> {event.location}</p>
                  <div style="display:flex;padding-top:10px;padding-bottom:10px;background-color:#bcbcbc;align-items:center">
                    <img src={event.logo} style="width:30px;height:30px;border-radius:50%;margin:0 10px"/>
                    <p>{event.org}</p>
                  </div>
                </div>
              </div>
            {/each}
          </div>
        </div>

        <div class="news" style="padding-top:40px;">
          <h1 style="margin-bottom:20px">Latest News</h1>
          <News />
        </div>
      </div>
    </div>

  {:else if selectedButton === "events"}
    <div class="view">
      <div class="form-view">
        {#if locationForm}
          <LocationForm bind:locationForm bind:onCampus bind:location {numAtt} bind:roomSelection bind:availableRooms bind:schedule/>
        {:else if createEvent}
          <EventForm bind:locationForm bind:createEvent bind:location bind:numAtt bind:availableRooms bind:startDate bind:startTime bind:endDate bind:endTime bind:eventTitle bind:eventOrg bind:privateEvent bind:eventCategory bind:eventPerks bind:eventDescription bind:schedule/>
        {:else}
          <button class="create-event-btn" on:click={() => createEvent=true}>Create New Event</button>
          <h1 style="margin-top:-20px">Events</h1>
          <Events />
        {/if}
      </div>
    </div>

  {:else if selectedButton === "orgs"}
    <div class="orgsection">
      {#if !selectedOrg}
        <h1>Organizations</h1>
        <div class="grid-view">
          <div class="selections">
            <div class="searchbox">
              <input type="text" placeholder="Search organizations..." bind:value={search} />  
            </div>

            <div class="category">
              {#each categories as cat}
                <label class="cat-option">
                  <input type="checkbox" bind:group={selectedCategory} value={cat} on:change={() => toggleCategory(cat)} />
                  {cat}
                </label>
              {/each}  
            </div>
          </div>

          <div class="org-cards">
            {#if search.trim() !== "" && filteredOrgs.length == 0}
              <p>No organizations found.</p>   
            {:else}
              <div class="stack">
                {#each filteredOrgs.length > 0 ? filteredOrgs : orgs as org}
                  <button class="orglist" on:click={() => openOrg(org)}>
                    <div class="org-content">
                      <div class="orgimg"> 
                        <img src={org.img} alt={org.name} />
                      </div>
                      <div class="orgname">
                        <p>{org.name}</p>
                      </div>
                    </div>
                  </button>
                {/each}
              </div>
            {/if}
          </div>
        </div>

      {:else}
        <div class="gobackbutton">
          <button class="goback" on:click={closeOrg}>Go back</button>
        </div>

        <div class="orgdet">
          <div class="orgdetcontent">
            <div class="orgheader">
              <div>
                <img src={selectedOrg.img} alt={selectedOrg.name} />
              </div>
              <div>
                <p>{selectedOrg.name}</p>
              </div>
            </div>
            <div class="jbutton">
              <button class="joinbutton" on:click={closeOrg}>JOIN</button>
            </div>
          </div>

          <div class="AdditionalInfo">
            <p class="DetHeaders">Who Are We?</p>
            <p class="description">{selectedOrg.description}</p>
            <p class="DetHeaders">Additional Information</p>
            <p class="addinfo"><strong>Meeting Days:</strong> {selectedOrg.meeting_days}</p>
            <p class="addinfo"><strong>Meeting Time:</strong> {selectedOrg.meeting_time}</p>
            <p class="DetHeaders">Get In Contact</p>
            <p class="addinfo"><strong>Contact Email:</strong> {selectedOrg.email}</p>

            <div class="roster">
              <p class="DetHeaders">Exec Roster</p>
              <div class="exec-grid">
                {#each selectedOrg.President as president}
                  <div class="execbox">
                    <p class="role"><strong>President</strong></p>
                    <p class="name">{president}</p>
                  </div>
                {/each}
                {#each selectedOrg.Vice_President as vpresident}
                  <div class="execbox">
                    <p class="role"><strong>Vice President</strong></p>
                    <p class="name">{vpresident}</p>
                  </div>
                {/each}
                {#each selectedOrg.Advisor as advisor}
                  <div class="execbox">
                    <p class="role"><strong>Advisor</strong></p>
                    <p class="name">{advisor}</p>
                  </div>
                {/each}
                {#each selectedOrg.Treasurer as treasurer}
                  <div class="execbox">
                    <p class="role"><strong>Treasurer</strong></p>
                    <p class="name">{treasurer}</p>
                  </div>
                {/each}
                {#each selectedOrg.Officers as officer}
                  <div class="execbox">
                    <p class="role"><strong>Officer</strong></p>
                    <p class="name">{officer}</p>
                  </div>
                {/each}
              </div>
            </div>
          </div>
        </div>
      {/if}
    </div>

  {:else if selectedButton === "news"}
    <div class="view">
      <h1>News</h1>
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
  .event { box-shadow:0 0 2px black; }
  .event:hover { box-shadow:0 0 5px black; }
</style>
