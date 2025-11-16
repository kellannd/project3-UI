<script>
  let news = {
    news: [
      {
        title: "University of Cincinnati ACM-W Student Chapter",
        date: "Friday, November 14, 2025",
        author: "John Smith",
        org: "CEAS Ambassadors",
        description:
          "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
        img: "../../../public/images/image.png",
      },
    ],
  };
</script>

<div class="flex-disp">
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
@import "../app.css"
</style>
