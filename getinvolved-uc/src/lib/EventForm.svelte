<script>
  export let schedule;

  export let locationForm;

  export let createEvent;

  export let location;

  // event form variables
  export let eventTitle;
  export let eventOrg;
  export let privateEvent;
  export let eventCatagory;
  export let eventPerks;
  export let eventDescription;

  export let numAtt;

  export let availableRooms;

  export let startDate;
  let formattedStartDate;

  export let startTime;
  let formattedStartTime;

  export let endDate;
  let formattedEndDate;

  export let endTime;
  let formattedEndTime;

  let daysofweek = [
    "Monday",
    "Tuesday",
    "Wednesday",
    "Thursday",
    "Friday",
    "Saturday",
    "Sunday",
  ];

  function formatStartDate() {
    formattedStartDate = new Date(startDate);
    formattedStartDate = daysofweek[formattedStartDate.getDay()];
  }

  function formatEndDate() {
    formattedEndDate = new Date(endDate);
    formattedEndDate = daysofweek[formattedEndDate.getDay()];
  }

  function to12Hour(time24) {
    let [hour, minute] = time24.split(":").map(Number);
    const suffix = hour >= 12 ? "PM" : "AM";

    hour = hour % 12;
    if (hour === 0) hour = 12;

    return `${hour}:${String(minute).padStart(2, "0")}${suffix}`;
  }

  function formatStartTime() {
    formattedStartTime = to12Hour(startTime);
  }

  function formatEndTime() {
    formattedEndTime = to12Hour(endTime);
  }

  function toMinutes(timeStr) {
    const [time, modifier] = timeStr.split(/(AM|PM)/);
    let [hours, minutes] = time.split(":").map(Number);

    if (modifier === "PM" && hours !== 12) hours += 12;
    if (modifier === "AM" && hours === 12) hours = 0;

    return hours * 60 + minutes;
  }

  function roomHasConflict(events, day, start, end) {
    const newStart = toMinutes(start);
    const newEnd = toMinutes(end);

    return events.some((event) => {
      if (event.date !== day) return false;

      const existingStart = toMinutes(event.start);
      const existingEnd = toMinutes(event.end);

      // true if the two time intervals overlap
      return newStart < existingEnd && newEnd > existingStart;
    });
  }

  function getAvailableRooms(schedule, day, start, end) {
    return Object.entries(schedule)
      .filter(([roomName, events]) => !roomHasConflict(events, day, start, end))
      .map(([roomName]) => roomName);
  }

  function getRooms() {
    availableRooms = getAvailableRooms(
      schedule,
      formattedStartDate,
      formattedStartTime,
      formattedEndTime
    );
  }

  function clearForms() {
    eventTitle = "";
    eventOrg = "studyroom";
    privateEvent = false;
    eventCatagory = "";
    eventPerks = "";
    eventDescription = "";
    numAtt = null;
    startDate = null;
    startTime = null;
    endDate = null;
    endTime = null;

        location = {
      title: "",
      address: "",
      city: "",
    };
  }

  function createNewEvent() {
    formatStartDate();
    formatStartTime();
    formatEndTime();
    schedule[location.title].push({
      date: formattedStartDate,
      start: formattedStartTime,
      end: formattedEndTime,
      title: eventTitle,
    });

    location = {
      title: "",
      address: "",
      city: "",
    };

    createEvent = false;

    clearForms()
  }

  function closeNewEvent(){
    createEvent = false;

    clearForms()
  }
</script>

<button
  class="close-btn"
  onclick={() => {
    closeNewEvent()
  }}><i class="bi bi-x-lg"></i></button
><br />
<div class="flex-disp" style="margin-left: -125px">
  <div>
    <div class="basic-details">
      <div
        style="padding-left: 50px; padding-right: 50px; padding-top: 25px; padding-bottom: 25px"
      >
        <label for="event-title"><span class="req">*</span>Event Title:</label
        ><br />
        <input
          bind:value={eventTitle}
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
          bind:value={eventOrg}
        >
          <option value="studyroom">Personal Use/Study Room</option>
          <option value="acmw"
            >University of Cincinnati ACM-W Student Chapter</option
          >
        </select><br /><br /><br />

        <label for="numAtt">Expected Number in Attendance:</label><br />
        <input
          bind:value={numAtt}
          type="number"
          id="numAtt"
          name="numAtt"
          style="width: 500px"
        /><br /><br /><br />

        {#if eventOrg && eventOrg != "studyroom"}
          <div>
            <input
              type="checkbox"
              id="display"
              name="display"
              bind:checked={privateEvent}
            />
            <label for="display">Make Event Private</label><br /><br /><br />

            <label for="catagory">Event Catagory:</label><br />
            <select
              id="catagory"
              name="catagory"
              style="width: 500px"
              bind:value={eventCatagory}
            >
              <option value=""></option>
              <option value="1">Catagory 1</option>
            </select><br /><br /><br />

            <label for="perks">Perks:</label>
            <select
              id="perks"
              name="perks"
              style="width:500px"
              bind:value={eventPerks}
            >
              <option value=""></option>
              <option value="food">Free Food</option>
              <option value="merch">Free Merch</option>
            </select><br /><br /><br />

            <label for="event-description"
              ><span class="req">*</span>Description:</label
            ><br />
            <textarea
              style="width: 500px; height: 300px"
              bind:value={eventDescription}
            ></textarea><br /><br /><br />
          </div>
        {/if}
      </div>
    </div>

    <div class="date-time">
      <div class="flex-disp">
        <div
          style="display: grid; grid-template-columns: 1fr 1fr; padding: 20px"
        >
          <div style="padding-right: 20px;">
            <label for="start-date"><span class="req">*</span>Start Date:</label
            ><br />

            <input
              onchange={() => {
                formatStartDate();
                location = {
                  title: "",
                  address: "",
                  city: "",
                };
              }}
              bind:value={startDate}
              type="date"
              id="start-date"
              name="start-date"
              class="date-time-input"
              style="margin-bottom: 20px"
            /><br />

            <label for="start-time"><span class="req">*</span>Start Time:</label
            ><br />
            <input
              onchange={() => {
                formatStartTime();
                location = {
                  title: "",
                  address: "",
                  city: "",
                };
              }}
              bind:value={startTime}
              type="time"
              id="start-time"
              name="start-time"
              class="date-time-input"
            />
          </div>

          <div style="padding-left: 20px">
            <label for="end-date"><span class="req">*</span>End Date:</label><br
            />

            <input
              onchange={() => {
                formatEndDate();
                location = {
                  title: "",
                  address: "",
                  city: "",
                };
              }}
              bind:value={endDate}
              type="date"
              id="end-date"
              name="end-date"
              class="date-time-input"
              style="margin-bottom: 20px"
              required
            /><br />

            <label for="end-time"><span class="req">*</span>End Time:</label><br
            />
            <input
              onchange={() => {
                formatEndTime();
                location = {
                  title: "",
                  address: "",
                  city: "",
                };
              }}
              bind:value={endTime}
              type="time"
              id="end-time"
              name="end-time"
              class="date-time-input"
            />
          </div>
        </div>
      </div>

      <div>
        {#if location.title}
          <div
            class="flex-disp"
            style="padding-top: 10px; padding-bottom: 20px; font-size: 20px"
          >
            <div>
              <i class="bi bi-geo-alt-fill" style="padding-right: 5px"></i>
            </div>
            <div>
              <p>{location.title}</p>
              <p>{location.address}</p>
              <p>{location.city}</p>
            </div>
          </div>
        {/if}
      </div>

      <div style="text-align: center">
        <button
          class="add-loc-btn"
          onclick={() => {
            locationForm = true;
            getRooms();
            location = {
              title: "",
              address: "",
              city: "",
            };
          }}>Add Location</button
        >
      </div>
    </div>
    <div style="text-align:center; margin-top: -80px; padding-bottom: 80px">
      <button
        class="add-loc-btn"
        style="width: 300px"
        onclick={() => {
          createNewEvent();
        }}>Create Event</button
      >
    </div>
  </div>
</div>

<style>
  @import "../app.css";
</style>
