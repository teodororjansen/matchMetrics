<script>
  let name = "";
  let age = 18;
  let height = 160;
  let Interesser = "";
  let Match = ["Du matcher perfekt med Teodor", "Du matcher med Teodor", "Du matcher ikke med Teodor"]


  const appName = "MatchMetrics";


  import earLength from "./assets/earLength.jpg";
  import chinLength from "./assets/chinLength.jpg";
  import shoulderLength from "./assets/shoulderLength.jpg";
  import armpitLength from "./assets/armpitLength.jpg";
  import midBackLength from "./assets/midBackLength.jpg";

  function handleSelectChange(event) {
    Interesser = event.target.value;
  }

  let totalScore = 0

  function calculateScore() {
    if (height < 150) {
      totalScore = totalScore - 1
    } else if (height >= 150 && height < 180) {
      totalScore = totalScore + 1
    } else {
      totalScore = totalScore - 2
    }

    if (age < 17) {
      totalScore = totalScore -2  
    } else if (age >= 18 && age <20){
      totalScore = totalScore + 1
    } else {
      totalScore = totalScore -1
    }
    
    if (Interesser === "fotball") {
      totalScore = totalScore + 2
    } else if (Interesser === "basketball") {
      totalScore = totalScore - 1
    } else if (Interesser === "håndball") {
      totalScore = totalScore - 2
    } else if (Interesser === "golf") {
      totalScore = totalScore + 4
    } else if (Interesser === "amerikansk fotball") {
      totalScore = totalScore + 0
    } else if (Interesser === "hockey") {
      totalScore = totalScore + 1
    } else if (Interesser === "tennis") {
      totalScore = totalScore + 2
    } else if (Interesser === "volleyball") {
      totalScore = totalScore + 1
    } else {
      totalScore = totalScore + 0
    }
  }

  function matching() {
    if (totalScore = 6) {
      return Match[0]
    } else if (totalScore < 6) {
      return Match[1]
    } else {
      return Match[2]
    }
  }

  

  
</script>

<main>
  <h1>Matcher du med Teo</h1>

  <div class="spørsmål">
    <label for="name"><h3>Hva heter du?</h3></label><br />
    <input type="text" bind:value={name} />
    <span>Hei, {name}</span>
  </div>

  <div class="spørsmål">
    <label for="age"><h3>Hvor gammel er du?</h3></label><br />
    <input type="range" min="12" max="100" bind:value={age} />
    <span>Age {age}</span>
  </div>

  <div class="spørsmål">
    <label for="height"><h3>Hvor høy er du?</h3></label> <br />
    <input type="range" min="120" max="210" bind:value={height} />
    <span>{height}cm</span>
  </div>

  <div class="spørsmål">
    <span><h3>Hvilken lengde har du på håret?</h3></span>
    <input type="radio" name="hairLength" value="earLength" id="earLength" />
    <label for="hairlength">
      <img src={earLength} width="170px" height="225px" class="hairLength" />
    </label>
    <input type="radio" name="hairLength" value="chinLength" id="chinLength" />
    <label for="hairLength">
      <img src={chinLength} width="170px" height="225px" class="hairLength" />
    </label>
    <input type="radio" name="hairLength" value="shoulderLength" id="shoulderLength" />
    <label for="hairLength">
      <img src={shoulderLength} width="170px" height="225px" class="hairLength"/>
    </label>
    <input type="radio" name="hairLength" value="armpitLength" id="armpitLength" />
    <label for="hairLength">
      <img src={armpitLength} width="170px" height="225px" class="hairLength" />
    </label>
    <input type="radio" name="hairLength" value="midBackLength" id="midBackLength" />
    <label for="hairLength">
      <img src={midBackLength} width="170px" height="225px" class="hairLength" />
    </label>
  </div>

  <div class="spørsmål">
    <label for="sport"><h3>Hva er din favoritt sport?</h3></label>
    <select name="sport" id="sport" on:change={handleSelectChange} bind:value={Interesser}>
      <option value="fotball">Fotball</option>
      <option value="basketball">Basketball</option>
      <option value="håndball">Håndball</option>
      <option value="golf">Golf</option>
      <option value="amerikansk fotball">Amerikansk fotball</option>
      <option value="hockey">Hockey</option>
      <option value="tennis">Tennis</option>
      <option value="volleyball">Volleyball</option>
    </select>
    <p>Du har valgt: {Interesser}</p>
  </div>

  <div class="spørsmål">
    <legend><h3>Hva liker du å gjøre på fritiden din</h3></legend>
      <div>
        <input type="checkbox" id="hobby" value="trening" name="trening" />
        <label for="trening">Trening</label>
      </div>
      <div>
        <input type="checkbox" id="hobby" value="fotball" name="fotball" />
        <label for="fotball">Fotball</label>
      </div>
      <div>
        <input type="checkbox" id="hobby" value="tennis" name="tennis" />
        <label for="tennis">Tennis</label>
      </div>
      <div>
        <input type="checkbox" id="hobby" value="gaming" name="gaming" />
        <label for="gaming">Gaming</label>
      </div>    
      <div>
        <input type="checkbox" id="hobby" value="fest" name="fest" />
        <label for="fest">Fest</label>
      </div>    
      <div>
        <input type="checkbox" id="hobby" value="golf" name="golf" />
        <label for="golf">Golf</label>
      </div>  
    </div>  
  

  <div class="spørsmål">
    <button on:click={calculateScore}>Calculate min score</button>
    <div>
      <label for="score"><h3>Din Score:</h3></label>
      <span>{totalScore}</span>
    </div>
  </div>

  <div class="spørsmål">
    <h3>Litt om oss(meg)</h3>
    <p>Hei! Jeg heter Teodor Ørjansen og akuratt nå studerer jeg Informasjonsteknologi 2 i tredje klasse på Vika videregående skole. Jeg øsnket å skape en ganske simpel app som ga deg noen spørsmål og kalkulerer om du matcher med meg eller ikke. Jeg har akuratt begynnt å lære om svelte.js og har lært mye av utviklingen til denne appen som jeg skal ta med meg videre til eventuelle nye og forbedret apper fremover. Du kan gjerne sende meg tilbakemeldinger på appen enten det er forbedringer eller tips som jeg kan ta nytte av videre. E-postadressen min ligger nedenfor. Takk for at du ville prøve appen min!:)</p>
    <p>Teodor Eiken Ørjansen</p>
    <p>sist endret: 14.10.2023</p>
    <p>E-postadresse: teoea001@osloskolen.no</p>
  </div>
  
  <button on:click={matching}>Sjekk om du matcher</button>

  <span>{matching}</span>
  
</main>

<!-- label {
    display: block;
    margin: 10px 0;
    cursor: pointer;
  }

  input[type="radio"] {
    display: none;
  }

  input[type="radio"]:checked + img {
    border: 2px solid #007bff; /* Highlight the selected image */
  }
  -->
<style>
</style>
