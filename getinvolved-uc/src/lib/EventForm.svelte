<script>
      let orgSelect = "";

      export let locationForm;

      export let createEvent;

</script>
<button
          class="close-btn"
            onclick={() => {
              createEvent = false;
            }}><i class="bi bi-x-lg"></i></button
          ><br />
<div style=" display: flex; justify-content: center;">
<div>

  <h1>Create Event</h1>

  <div class="basic-details">
    <div
      style="padding-left: 50px; padding-right: 50px; padding-top: 25px; padding-bottom: 25px"
    >
      <label for="event-title"><span class="req">*</span>Event Title:</label><br
      />
      <input
        type="text"
        id="event-title"
        name="event-title"
        style="width: 500px"
      /><br /><br /><br />

      <label for="org">Who is this event for?:</label><br />
      <select
        id="org"
        name="org"
        style="width: 500px; font-size: 20px"
        bind:value={orgSelect}
        onchange={() => {
          console.log(orgSelect);
        }}
      >
        <option value="studyroom">Personal Use/Study Room</option>
        <option value="acmw"
          >University of Cincinnati ACM-W Student Chapter</option
        >
      </select><br /><br /><br />

      <label for="numAtt">Expected Number in Attendance:</label><br>
      <input type="number" id="numAtt" name="numAtt" style="width: 500px"><br><br><br>

      {#if orgSelect && orgSelect != "studyroom"}
        <div>
          <input type="checkbox" id="display" name="display" />
          <label for="display">Make Event Private</label><br /><br /><br />

          <label for="catagory">Event Catagory:</label><br />
          <select id="catagory" name="catagory" style="width: 500px">
            <option value=""></option>
            <option value="1">Catagory 1</option>
          </select><br /><br /><br />

          <label for="perks">Perks:</label>
          <select id="perks" name="perks" style="width:500px">
            <option value=""></option>
            <option value="food">Free Food</option>
            <option value="merch">Free Merch</option>
          </select><br /><br /><br />


      <label for="event-description"
        ><span class="req">*</span>Description:</label
      ><br />
      <textarea style="width: 500px; height: 300px"></textarea><br /><br /><br
      />
           </div>
      {/if}
    </div>
  </div>

  <div class="date-time">
    <h2 style="font-weight:lighter;">Time and Place</h2>
    <div style="display: grid; grid-template-columns: 1fr 1fr; padding: 20px">
      <div>
        <label for="start-date"><span class="req">*</span>Start Date:</label><br
        />

        <input
          type="date"
          id="start-date"
          name="start-date"
          class="date-time-input"
          style="margin-bottom: 20px"
        /><br />

        <label for="start-time"><span class="req">*</span>Start Time:</label><br
        />
        <input
          type="time"
          id="start-time"
          name="start-time"
          class="date-time-input"
        />
      </div>

      <div>
        <label for="end-date"><span class="req">*</span>End Date:</label><br />

        <input
          type="date"
          id="end-date"
          name="end-date"
          class="date-time-input"
          style="margin-bottom: 20px"
          required
        /><br />

        <label for="end-time"><span class="req">*</span>End Time:</label><br />
        <input
          type="time"
          id="end-time"
          name="end-time"
          class="date-time-input"
        />
      </div>
    </div>

    <button onclick={() => {locationForm = true
    }}>Location</button>
  </div>
  </div>
  </div>

<style>
    @import "../app.css";
  .date-time-input {
    width: 200px;
    font-size: 25px;
  }

  label {
    font-size: 20px;
  }

  .req {
    color: red;
  }

  .date-time {
    border-style: solid;
    border-width: 1px;
    border-color: black;
    width: 600px;
    height: 400px;
    padding: 20px;
  }

  .basic-details {
    border-style: solid;
    border-width: 1px;
    border-color: black;
    width: 600px;
    margin-bottom: 50px
  }

  input,
  select,
  textarea {
    padding: 10px;
    font-size: 20px;
    border-radius: 5px;
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
