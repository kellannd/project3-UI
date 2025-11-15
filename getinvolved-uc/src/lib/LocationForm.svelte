<script>
  export let locationForm;

  export let onCampus;

  export let location;

  function testOnlineLocation() {
    location.title = "Online Location";
    location.address = "https://google.com";
  }


  // off campus
  let offCampusTitle = ""
  let offCampusAddress = ""
  let offCampusCity = ""
  let offCampusState = ""

  // online
  let onlineLink = ""

  function offCampusLocation() {
    location.title = offCampusTitle;
    location.address = offCampusAddress;
    location.city = offCampusCity + ", " + offCampusState

  }

  function onlineLocation() {
    location.title = "Online Location"
    location.address = onlineLink
  }
</script>

<button
  class="close-btn"
  onclick={() => {
    locationForm = false;
  }}><i class="bi bi-x-lg"></i></button
><br />

<div>
<div class="flex-disp">
  <div>
    <div class="location">
      <div class="flex-disp">
        <button
          onclick={() => {
            onCampus = "oncampus";
          }}
          class="location-btn {onCampus === 'oncampus' ? 'selected' : ''}"
          >On Campus</button
        >
        <button
          onclick={() => {
            onCampus = "offcampus";
          }}
          class="location-btn {onCampus === 'offcampus' ? 'selected' : ''}"
          >Off Campus</button
        >
        <button
          onclick={() => {
            onCampus = "online";
          }}
          class="location-btn {onCampus === 'online' ? 'selected' : ''}"
          >Online</button
        >
      </div>

      {#if onCampus === "offcampus"}
      <div class="off-campus-inputs">
        <div>
        <label for="loc-name"><span class="req">*</span>Location Name:</label
        ><br />
        <input
        bind:value={offCampusTitle}
          type="text"
          id="loc-name"
          name="loc-name"
          style="width: 500px"
        /><br /><br /><br />

        <label for="loc-address"><span class="req">*</span>Address:</label><br
        />
        <input
        bind:value={offCampusAddress}
          type="text"
          id="loc-address"
          name="loc-address"
          style="width: 500px"
        /><br /><br /><br />

        <label for="loc-city">City:</label><br />
        <input
        bind:value={offCampusCity}
          type="text"
          id="loc-city"
          name="loc-city"
          style="width: 500px"
        /><br /><br /><br />

        <label for="loc-state">State or Province:</label><br />
        <input
        bind:value={offCampusState}
          type="text"
          id="loc-staet"
          name="loc-state"
          style="width: 500px"
        /><br /><br /><br />

        <div style="text-align: center">
        <button class="add-loc-btn" onclick = {() => offCampusLocation() }>Add Location</button>
        </div>
        </div>
        </div>
      {:else if onCampus === "online"}
      <div class="online-inputs">
        <div>
        <label for="online-link">Online Location Link:</label><br />
        <input
        bind:value={onlineLink}
          type="text"
          id="online-link"
          name="online-link"
          style="width: 500px"
        /><br /><br /><br />

        <label for="online-instructions"
          >Online Location Instructions for Attendees:</label
        ><br />
        <textarea
          id="online-instructions"
          name="online-instructions"
          style="width: 500px"
        ></textarea><br><br /><br />

        <div style="text-align: center">
        <button class="add-loc-btn" onclick={() => onlineLocation() }>Add Location</button>
        </div>
        </div>
        </div>
      {/if}
    </div>
  </div>
</div>
</div>

<style>
  @import "../app.css";
</style>
