<script>
  export let selectedButton;
  export let createEvent;
</script>

<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.2/font/bootstrap-icons.css"
/>

<div class="sidebar">
  <div class="icon-div {selectedButton === 'home' ? 'active' : ''}">
    <button
      class="sidebar-btn"
      onclick={() => {
        selectedButton = "home";
        createEvent = false;
      }}
    >
      <i class="bi bi-house sidebar-icon"></i><br />
      <p>Home</p>
    </button>
  </div>

  <div class="icon-div {selectedButton === 'events' ? 'active' : ''}">
    <button
      class="sidebar-btn"
      onclick={() => {
        selectedButton = "events";
        createEvent = false;
      }}
    >
      <i class="bi bi-calendar-event sidebar-icon"></i><br />
      <p>Events</p>
    </button>
  </div>

  <div class="icon-div {selectedButton === 'orgs' ? 'active' : ''}">
    <button
      class="sidebar-btn"
      onclick={() => {
        selectedButton = "orgs";
        createEvent = false;
      }}
    >
      <i class="bi bi-people sidebar-icon"></i><br />
      <p>Orgs</p>
    </button>
  </div>
  <div class="icon-div {selectedButton === 'news' ? 'active' : ''}">
    <button
      class="sidebar-btn"
      onclick={() => {
        selectedButton = "news";
        createEvent = false;
      }}
    >
      <i class="bi bi-newspaper sidebar-icon"></i><br />
      <p>News</p>
    </button>
  </div>
  <div class="icon-div {selectedButton === 'forms' ? 'active' : ''}">
    <button
      class="sidebar-btn"
      onclick={() => {
        selectedButton = "forms";
        createEvent = false;
      }}
    >
      <i class="bi bi-files sidebar-icon"></i><br />
      <p>Forms and</p>
      <p>Links</p>
    </button>
  </div>
</div>

<style>
  @import "../app.css";
</style>
