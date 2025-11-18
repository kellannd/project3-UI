<script>
  let orgs = {
    orgs: [
    {
      logo: aclogo,
        name: "Animation Club",
        description:
          "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.",
      },
      {
logo: ccat,
        name: "Community Action Team",
        description:
          "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.",
      },

    {
logo: nsbe,
        name: "National Society of Black Engineers at University of Cincinnati",
        description:
          "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.",
      },
          {
logo: acmwlogo,
        name: "University of Cincinnati ACM-W Student Chapter",
        description:
          "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.",
      },
    ],
  };



  import acmwlogo from "../../public/logosimgs/acmw.jpg";
  import ccat from "../../public/logosimgs/communityaction.jpg";
  import nsbe from "../../public/logosimgs/nsbe.jpg";
  import aclogo from "../../public/logosimgs/ucanimationclub.jpg";

  let logos = [aclogo, acmwlogo]
</script>

<div class="flex-disp" style=" flex-wrap: wrap;">
  {#each orgs.orgs as org}
    <div class="org-info" style="margin-bottom: 20px">
      <div>
        <img
          src={org.logo}
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
