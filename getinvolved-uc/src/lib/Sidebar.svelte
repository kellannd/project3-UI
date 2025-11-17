<script>
  export let selectedButton;
  export let createEvent;
  import logo from "../assets/image.png";
</script>

<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.2/font/bootstrap-icons.css"
/>

<div class="navbar">
  <div class="side-left">
    <img src={logo} class="logo" alt="Involved UC logo" />
  </div>

  <div class="nav-center">
    <div class="icon-div {selectedButton === 'home' ? 'active' : ''}">
      <button
        class="sidebar-btn"
        onclick={() => {
          selectedButton = "home";
          createEvent = false;
        }}
      >
        <i class="bi bi-house sidebar-icon"></i><!--<br />-->
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
        <i class="bi bi-calendar-event sidebar-icon"></i><!--<br />-->
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
        <i class="bi bi-people sidebar-icon"></i> <!---<br />-->
        <p>Orgs</p>
      </button>
    </div>
    <!----<div class="icon-div {selectedButton === 'news' ? 'active' : ''}">
      <button
        class="sidebar-btn"
        onclick={() => {
          selectedButton = "news";
          createEvent = false;
        }}
      >
        <i class="bi bi-newspaper sidebar-icon"></i>
        <p>News</p>
      </button>
    </div>-->
    <div class="icon-div {selectedButton === 'forms' ? 'active' : ''}">
      <button
        class="sidebar-btn"
        onclick={() => {
          selectedButton = "forms";
          createEvent = false;
        }}
      >
        <i class="bi bi-files sidebar-icon"></i><!---<br />-->
        <p>Forms and</p>
        <p>Links</p>
      </button>
    </div>
  </div>
  <div class="side-right">
    <i class="bi bi-person-circle user-icon"></i>
  </div>
</div>

<style>
  @import "../app.css";
.navbar {
    position: fixed;
    width: 100vw;
    height: 80px;
    background-color: white;
    border-bottom-style: solid;
    border-bottom-color: lightgrey;
    border-bottom-width: 2px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    z-index: 1000;
    padding: 0 20px;
}

.user-icon {
    font-size: 40px;
    position: absolute;
    right: 0;
    top: 0;
    padding-right: 40px;
    padding-top: 20px
}

.logo {
    height: 50px;
}

/* .side-left, .side-right {
  display: flex;
  align-items: center;
  flex-shrink: 0;
} */
.nav-center {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-grow: 1;
  margin-right: 250px;
}
.icon-div {
  display: flex;
  align-items: center;
  flex-direction: column;
}

</style>
