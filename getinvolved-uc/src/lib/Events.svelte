<script>
  let events = {
    events: [
      {
        title: "New Event",
        date: "Friday, November 14 at 6:30PM",
        img: "../../../public/images/image.png",
        location: "Student Center",
        org: "ACM-W",
      },
      {
        title: "New Event",
        date: "Friday, November 14 at 6:30PM",
        img: "../../../public/images/image.png",
        location: "Student Center",
        org: "ACM-W",
      },
      {
        title: "New Event",
        date: "Friday, November 14 at 6:30PM",
        img: "../../../public/images/image.png",
        location: "Student Center",
        org: "ACM-W",
      },
      {
        title: "New Event",
        date: "Friday, November 14 at 6:30PM",
        img: "../../../public/images/image.png",
        location: "Student Center",
        org: "ACM-W",
      },
    ],
  };

  import acmwlogo from "../assets/acmw.jpg";
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
            src={acmwlogo}
            style="width: 30px; height: 30px; border-radius: 50%; margin-left: 10px; margin-right: 10px"
          />
          <p>ACM-W</p>
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
