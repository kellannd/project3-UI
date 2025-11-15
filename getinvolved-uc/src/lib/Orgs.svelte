<script>
  let orgs = {
    orgs: [
      {
        name: "University of Cincinnati ACM-W Student Chapter",
        description:
          "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.",
      },
    ],
  };

  import acmwlogo from "../assets/acmw.jpg";
</script>

<div class="flex-disp">
  {#each orgs.orgs as org}
    <div class="org-info">
      <div>
        <img
          src={acmwlogo}
          style="width: 75px; height: 75px; border-radius: 50%; margin-right: 20px"
        />
      </div>

      <div>
        <h3 style="padding-bottom: 10px">{org.name}</h3>
        <p>{org.description}</p>
      </div>
    </div>
  {/each}
</div>

<style>
@import "../app.css";
</style>
