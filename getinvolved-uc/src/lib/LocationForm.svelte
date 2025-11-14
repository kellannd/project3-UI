<script>
  export let locationForm;

  export let onCampus;
</script>

<button
  class="close-btn"
  onclick={() => {
    locationForm = false;
  }}><i class="bi bi-x-lg"></i></button
><br />
<div style=" display: flex; justify-content: center;">
  <div>

    <div class="location">
      <div style="display: flex; justify-content: center">
        <button onclick={() => {onCampus = "oncampus"
        }} class="location-btn" autofocus>on campus</button>
        <button onclick={() => {onCampus = "offcampus"
        }} class="location-btn">off campus</button>
        <button onclick={() => {onCampus = "online"}} class="location-btn">online</button>
      </div>

      {#if onCampus === "offcampus"}
        <label for="loc-name"><span class="req">*</span>Location Name:</label><br>
        <input type="text" id="loc-name" name="loc-name" style="width: 500px"/><br>

        <label for="loc-address"><span class="req">*</span>Address:</label><br>
        <input type="text" id="loc-address" name="loc-address" style="width: 500px"/><br>

        <label for="loc-city">City:</label><br>
        <input type="text" id="loc-city" name="loc-city" style="width: 500px"/><br>

        <label for="loc-state">State or Province:</label><br>
        <input type="text" id="loc-staet" name="loc-state" style="width: 500px"/><br>

        {:else if onCampus === "online"}
        <label for="online-link">Online Location Link:</label><br>
        <input type="text" id="online-link" name="online-link" style="width: 500px"><br>


        <label for="online-instructions">Online Location Instructions for Attendees:</label><br>
        <textarea id="online-instructions" name="online-instructions" style="width: 500px"></textarea>


      {/if}
    </div>
  </div>
</div>

<style>
  @import "../app.css";

  .location {
    border-style: solid;
    border-width: 1px;
    border-color: black;
    width: 1000px;
    height: 400px;
    padding: 20px;
  }

  .location-btn {
    padding: 10px;
    margin: 10px;
  }

  .location-btn:focus {
    background-color: red
  }
</style>
