<script>
    import Header from "./lib/Header.svelte";
    import Sidebar from "./lib/Sidebar.svelte";
    import odata from "./data/orgs.json";

    let selectedButton = "home"
    let selectedOrg = null;
    const orgs = odata[0].organizations;

    let search = "";
    let selectedCategory = [];

    const categories = [
      "Select All", ...new Set(orgs.map(org => org.category))
    ];

    function openOrg(org){
      selectedOrg = org;
    }

    function closeOrg(){
      selectedOrg = null;
    }

   $: filteredOrgs = orgs.filter(org => {
    const matchesSearch = org.name.toLowerCase().includes(search.toLowerCase());

    const matchesCategory =
      selectedCategory.length === 0 || selectedCategory.includes(org.category);

    return matchesSearch && matchesCategory;
});

</script>

<main>
  <Sidebar bind:selectedButton/>
  <Header />


  {#if selectedButton === "home"}
  <div class="view">
    <h1>home</h1>
  </div>

  {:else if selectedButton === "orgs"}
    <div class="orgsection">
      {#if !selectedOrg}
        <h1>Organizations</h1>
        <div class="grid-view">
          <div class="selections">
            <div class="searchbox">
              <input type="text" placeholder="Search organizations..." bind:value={search} />  
            </div>

            <div class="category">
              {#each categories as cat}
                <label class="cat-option"><input type="checkbox" bind:group={selectedCategory} value={cat}/>{cat}</label>
              {/each}  
            </div>
          </div>
        

          <div class="org-cards">
            {#if search.trim() !== "" && filteredOrgs.length == 0}
              <p>No organizations found.</p>   
            {:else}
              <div class="stack">
                {#each filteredOrgs.length > 0 ? filteredOrgs : orgs as org}
                  <button class="orglist" on:click={() => openOrg(org)}>
                    <div class="org-content">
                      <div class="orgimg"> 
                        <img src={org.img} alt={org.name} />
                      </div>
                      <div class="orgname">
                        <p>{org.name}</p>
                      </div>
                    </div>

                  </button>
                {/each}
              </div>

            {/if}
          </div>
        </div>
      {:else}
        <div class="gobackbutton">
          <button class="goback" on:click={closeOrg}>Go back</button>
        </div>
        <div class="orgdet">
          <div class="orgdetcontent">
            <div class="orgheader">
              <div>
                <img src={selectedOrg.img} alt={selectedOrg.name} />
              </div>
              <div>
                <p>{selectedOrg.name}</p>
              </div>
            </div>
            <div class="jbutton">
              <button class="joinbutton" on:click={closeOrg}>JOIN</button>
            </div>
            
          </div>

          <div class="AdditionalInfo">
            <p class="DetHeaders">Who Are We?</p>
            <p class="description">{selectedOrg.description}</p>
            <p class="DetHeaders">Additional Information</p>
            <p class="addinfo"><strong>Meeting Days: {selectedOrg.meeting_days}</strong> </p>
            <p class="addinfo"><strong>Meeting Time: {selectedOrg.meeting_time}</strong></p>
            <p class="DetHeaders">Get In Contact</p>
            <p class="addinfo"><strong>Contact Email: {selectedOrg.email}</strong></p>
            <div class="roster">
              <p class="DetHeaders">Exec Roster</p>
              <div class="exec-grid">
                {#each selectedOrg.President as president}
                  <div class="execbox">
                    <p class="role"><strong>President</strong></p>
                    <p class="name">{president}</p>
                  </div>
                {/each}

                {#each selectedOrg.Vice_President as vpresident}
                  <div class="execbox">
                    <p class="role"><strong>Vice President</strong></p>
                    <p class="name">{vpresident}</p>
                  </div>
                {/each}

                {#each selectedOrg.Advisor as advisor}
                  <div class="execbox">
                    <p class="role"><strong>Advisor</strong></p>
                    <p class="name">{advisor}</p>
                  </div>
                {/each}

                {#each selectedOrg.Treasurer as treasurer}
                  <div class="execbox">
                    <p class="role"><strong>Treasurer</strong></p>
                    <p class="name">{treasurer}</p>
                  </div>
                {/each}

                {#each selectedOrg.Officers as officer}
                  <div class="execbox">
                    <p class="role"><strong>Officer</strong></p>
                    <p class="name">{officer}</p>
                  </div>
                {/each}
              </div>
            </div>
          </div>

          
        </div>
        
        
      {/if}
    </div>
    
    


 {:else if selectedButton === "news"}
  <div class="view">
    <h1>news</h1>
  </div>

  {:else}
  <div class="view">
    <h1>forms</h1>
  </div>

  {/if}
</main>


