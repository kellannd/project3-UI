<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.2/font/bootstrap-icons.css"
/>

<script>
    // export let changeView;

    export let selectedButton;
</script>

<div class="sidebar">
  <div class="icon-div {selectedButton === 'home' ? 'active' : ''}">
    <button class="sidebar-btn" onclick={() => selectedButton = "home"}>
      <i class="bi bi-calendar-event sidebar-icon"></i><br />
      <p>Home</p>
    </button>
  </div>

  <div class="icon-div {selectedButton === 'orgs' ? 'active' : ''}">
    <button class="sidebar-btn" onclick={() => selectedButton = "orgs"}>
    <i class="bi bi-people sidebar-icon"></i><br />
    <p>Orgs</p>
    </button>
  </div>
  <div class="icon-div">
    <button class="sidebar-btn" onclick={() => selectedButton = "news"}>
    <i class="bi bi-newspaper sidebar-icon"></i><br />
    <p>News</p>
    </button>
  </div>
  <div class="icon-div">
    <button class="sidebar-btn" onclick={() => selectedButton = "forms"}>
    <i class="bi bi-files sidebar-icon"></i><br />
    <p>Forms</p>
    </button>
  </div>
</div>

<style>
  .sidebar {
    position: fixed;
    width: 100px;
    height: 100vh;
    background-color: white;
    border-right-style: solid;
    border-right-color: #e0e0e0;
    border-right-width: 2px;
    padding-top: 80px;
  }

  .active {
    background-color: #f0f4fb
  }

  .active .sidebar-btn:hover {
    background-color: #e6effa;
  }

  .sidebar-icon {
    font-size: 40px;
  }

  .icon-div {
    text-align: center;
  }
  .sidebar-btn {
    background-color: transparent;
    outline: none;
    cursor: pointer;
    border: none;
    width: 100px;
    height: 80px;
  }

  .sidebar-btn:hover {
    background-color: #f5f5f5;
    width: 99px;
  }
</style>
