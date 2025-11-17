<script>
    export let schedule;

    export let roomSelection;

    let daysofweek = [
    "Sunday",
    "Monday",
    "Tuesday",
    "Wednesday",
    "Thursday",
    "Friday",
    "Saturday"
  ];

    let today;

    function getToday(){
        today = new Date();
        today = today.getDay()
        return daysofweek[today]
    }

    getToday()
</script>

<div class="calendar-grid">
    <div>
        <h3 class="calendar-header {getToday() === 'Sunday' ? 'today' : ''}">Sunday</h3>
    </div>
    <div>
        <h3 class="calendar-header {getToday() === 'Monday' ? 'today' : ''}">Monday</h3>
    </div>
    <div>
        <h3 class="calendar-header {getToday() === 'Tuesday' ? 'today' : ''}">Tuesday</h3>
    </div>
    <div>
        <h3 class="calendar-header {getToday() === 'Wednesday' ? 'today' : ''}">Wednesday</h3>
    </div>
    <div>
        <h3 class="calendar-header {getToday() === 'Thursday' ? 'today' : ''}">Thursday</h3>
    </div>
    <div>
        <h3 class="calendar-header {getToday() === 'Friday' ? 'today' : ''}">Friday</h3>
    </div>
    <div>
        <h3 class="calendar-header {getToday() === 'Saturday' ? 'today' : ''}">Saturday</h3>
    </div>

    <div>
                {#each schedule[roomSelection] as entry}
            {#if entry.date === "Sunday"}
            <div class="event-entry">
                <p>{entry.start} - {entry.end}</p>
                <p>{entry.title}</p>

                <p>{roomSelection}</p>
                </div>
            {/if}
        {/each}
    </div>
    <div>
        {#each schedule[roomSelection] as entry}
            {#if entry.date === "Monday"}
            <div class="event-entry">
                <p>{entry.start} - {entry.end}</p>
                <p>{entry.title}</p>

                <p>{roomSelection}</p>
                </div>
            {/if}
        {/each}
    </div>

    <div>
        {#each schedule[roomSelection] as entry}
            {#if entry.date === "Tuesday"}
            <div class="event-entry">
                <p>{entry.start} - {entry.end}</p>
                <p>{entry.title}</p>

                <p>{roomSelection}</p>
                </div>
            {/if}
        {/each}
    </div>

    <div>
                {#each schedule[roomSelection] as entry}
            {#if entry.date === "Wednesday"}
            <div class="event-entry">
                <p>{entry.start} - {entry.end}</p>
                <p>{entry.title}</p>

                <p>{roomSelection}</p>
                </div>
            {/if}
        {/each}
    </div>

    <div>
                {#each schedule[roomSelection] as entry}
            {#if entry.date === "Thursday"}
            <div class="event-entry">
                <p>{entry.start} - {entry.end}</p>
                <p>{entry.title}</p>

                <p>{roomSelection}</p>
                </div>
            {/if}
        {/each}
    </div>

    <div>
                {#each schedule[roomSelection] as entry}
            {#if entry.date === "Friday"}
            <div class="event-entry">
                <p>{entry.start} - {entry.end}</p>
                <p>{entry.title}</p>

                <p>{roomSelection}</p>
                </div>
            {/if}
        {/each}
    </div>

    <div>
                {#each schedule[roomSelection] as entry}
            {#if entry.date === "Saturday"}
            <div class="event-entry">
                <p>{entry.start} - {entry.end}</p>
                <p>{entry.title}</p>

                <p>{roomSelection}</p>
                </div>
            {/if}
        {/each}
    </div>

</div>

<style>
    .calendar-grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
    grid-template-rows: 1fr 5fr;
    border-color: black;
    border-width: 2px;
    border-style: solid;
    width: 1400px;
    }

    .event-entry {
        background-color: lightblue;
        border-radius: 5px;
        margin: 5px;
        padding-top: 5px;
        padding-bottom: 5px;
        padding-left: 10px;
    }

    .calendar-header {
        color: white;
        background-color: cornflowerblue;
        padding-top: 10px;
        padding-bottom: 10px;
        text-align: center;
    }

    .today {
        background-color: navy
    }
</style>
