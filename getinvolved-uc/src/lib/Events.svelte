<script>
  import events from "./eventsdata.js"
  
</script>

<div style="display: flex; flex-wrap: wrap">
  {#each events.events as event}
    <div style="padding-left: 40px; padding-top: 40px">
      <div class="event"
      >
        <img src={event.img} style="width: 400px; height: 250px;" />
        <div style="height: 60px">
          <h3 style="padding: 15px">{event.title}</h3>
        </div>

        <p style="padding-left: 15px; padding-bottom: 10px"><i class="bi bi-calendar-event"></i>  {event.date}</p>
        <p style="padding-left: 15px; padding-bottom: 20px"><i class="bi bi-geo-alt-fill"></i>  {event.location}</p>

        <div
          style="display: flex; padding-top: 10px; padding-bottom: 10px ; background-color: #bcbcbc; align-items: center"
        >
          <img
            src={event.logo}
            style="width: 30px; height: 30px; border-radius: 50%; margin-left: 10px; margin-right: 10px"
          />
          <p>{event.org}</p>
        </div>
      </div>
    </div>
  {/each}
</div>

<style>
    .event {
        box-shadow: 0px 0px 2px black;
    }

    .event:hover {
         box-shadow: 0px 0px 5px black;
    }
</style>
