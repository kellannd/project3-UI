<script>
  export let locationForm;

  export let onCampus;

  export let location;

  export let numAtt;

  export let roomSelection;

  export let availableRooms;

  export let schedule;

  // off campus
  let offCampusTitle = "";
  let offCampusAddress = "";
  let offCampusCity = "";
  let offCampusState = "";

  // online
  let onlineLink = "";

  function offCampusLocation() {
    location.title = offCampusTitle;
    location.address = offCampusAddress;
    location.city = offCampusCity + ", " + offCampusState;

    locationForm = false
  }

  function onlineLocation() {
    location.title = "Online Location";
    location.address = onlineLink;

    locationForm = false;
  }

  function onCampusLocation(){
    location.title = roomSelection

    locationForm = false;
  }

  import rooms from "../assets/rooms.json";
  import Calendar from "./Calendar.svelte";

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
              <label for="loc-name"
                ><span class="req">*</span>Location Name:</label
              ><br />
              <input
                bind:value={offCampusTitle}
                type="text"
                id="loc-name"
                name="loc-name"
                style="width: 500px"
              /><br /><br /><br />

              <label for="loc-address"><span class="req">*</span>Address:</label
              ><br />
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
                <button class="add-loc-btn" onclick={() => offCampusLocation()}
                  >Add Location</button
                >
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
              ></textarea><br /><br /><br />

              <div style="text-align: center">
                <button class="add-loc-btn" onclick={() => onlineLocation()}
                  >Add Location</button
                >
              </div>
            </div>
          </div>
        {:else}
        <div style="text-align:center;">
          <select style="width: 500px; margin-bottom: 20px" bind:value={roomSelection} onchange={() => {
            console.log(roomSelection);
          }}>
            {#each rooms.rooms as room}
              {#if room.occ >= numAtt && availableRooms.includes(room.name)}
                <option value={room.name}>{room.name}</option>
              {/if}
            {/each}
          </select>
</div>
          {#if roomSelection}
          <Calendar bind:roomSelection bind:schedule/>
          {/if}

                                  <div style="text-align: center; margin-top: 20px">
                <button class="add-loc-btn" onclick={() => {onCampusLocation()
                  roomSelection = ""
                }}
                  >Add Location</button
                >
              </div>
        {/if}
      </div>
    </div>
  </div>
</div>

<style>
  @import "../app.css";
</style>
