<script>
    export let schedule;

    export let roomSelection;
</script>

<div class="calendar-grid">
    <div>
        <h3>Sunday</h3>
    </div>
    <div>
        <h3>Monday</h3>
    </div>
    <div>
        <h3>Tuesday</h3>
    </div>
    <div>
        <h3>Wednesday</h3>
    </div>
    <div>
        <h3>Thursday</h3>
    </div>
    <div>
        <h3>Friday</h3>
    </div>
    <div>
        <h3>Saturday</h3>
    </div>

    <div>

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
        margin: 1px;
        padding-top: 5px;
        padding-bottom: 5px;
        padding-left: 10px;
    }
</style>
