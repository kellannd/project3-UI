<script>
  let news = {
    news: [
      {
        title: "Do Good with Chipotle: Support the Bearcats Excercise Science Alliance",
        date: "Wednesday, November 5, 2025",
        author: "Tanna landers",
        org: "Bearcats Exercise Science Alliance",
        description:
          "Support BESA at Chiptole's Do Good With Chipotle fundraiser! Join us Sat, Nov 22, 4-8 PM at 2507 Clifton Ave or order pickup. Every meal helps fund BESA events and student opportunities.",
        img: "../../../public/newimgs/news1.png",
      },
      {
       title: "Personal Hygiene Drive",
        date: "Monday, November 3, 2025",
        author: "Kennedy Klaer",
        org: "Global Public Health Brigades - UC Chapter",
        description:
          "Come donate for good cause!",
        img: "../../../public/newimgs/NewsTwo.png",
      },
      {
       title: "Off campus volunteer opportunities!",
        date: "Monday, October 6, 2025",
        author: "Kennedy Klaer",
        org: "CEAS AmbassadorsGlobal Public Health Brigades - UC Chapter",
        description:
          "Information and links for upcoming volunteer opportunities opportunities.",
        img: "../../../public/newimgs/news3.png",
      },
    ],
  };
</script>

<div class="flex-disp" style="flex-direction: column;
  gap: 25px; max-width: 87%; padding-left: 40px">
{#each news.news as article}

<div class="article-info">
    <div>
        <img src={article.img} class="article-img"/>
    </div>

    <div class="article-info-text">
        <h3 class="article-title">{article.title}</h3>
        <p>{article.date}</p>
        <p class="article-author">Posted by {article.author} for {article.org}</p><br>
        <p>{article.description}</p>
    </div>
</div>
{/each}
</div>

<style>
  @import "../app.css";
</style>
