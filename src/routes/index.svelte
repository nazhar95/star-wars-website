<script>
    let id="";
    let name="";
    let gender="";
    let homeworld="";
    let height="";
    let weight="";
    let hair_color="";
    let eye_color="";
    let birth_year="";
    let description="";
    
    async function getInfo() {
        fetch('https://www.swapi.tech/api/people/' + id)
            .then((response) => response.json())
            .then((data) => {
                name = data.name; 
                gender = data.gender;
                homeworld = data.homeworld; 
                height = data.height; 
                weight = data.mass; 
                hair_color = data.hair_color; 
                eye_color = data.eye_color;
                birth_year = data.birth_year;
                description = data.description;  
            });
    }

</script>

<div class="container-fluid bg-dark text-light p-5 text-center">
   <h1>Star Wars 101</h1>
</div>

<div class="container text-center mt-3">
    <h2>Type in a character's ID</h2>

    <form on:submit|preventDefault={getInfo}>
        <label for="ID">Character ID:</label>
        <input id="id" bind:value={id} type="text" />
        <button type="submit">Check</button>
    </form>
    
    <div class="card text-white bg-primary">
        <div class="card-header">Name: {name}</div>
            <div class="card-body">
                <h5 class="card-title">Info:</h5>
                <p class="card-text">Gender: {gender}</p>
                <p class="card-text">Homeworld: {homeworld}</p>
                <p class="card-text">Height: {height}cm</p>
                <p class="card-text">Weight: {weight}kg</p>
                <p class="card-text">Hair color: {hair_color}</p>
                <p class="card-text">Eye color: {eye_color}</p>
                <p class="card-text">Birth year: {birth_year}</p>
                <p class="card-text">Description: {description}</p>
            </div>
        </div>
    </div>

