<script>
    let uid="";
    let name="";
    let gender="";
    let height="";
    let weight="";
    let hair_color="";
    let eye_color="";
    let birth_year="";
    
    async function getInfo() {
        fetch('https://www.swapi.tech/api/people/' + uid)
            .then((response) => response.json())
            .then((data) => {
                name = data.result.properties.name; 
                gender = data.result.properties.gender;
                height = data.result.properties.height; 
                weight = data.result.properties.mass; 
                hair_color = data.result.properties.hair_color; 
                eye_color = data.result.properties.eye_color;
                birth_year = data.result.properties.birth_year;
            });
    }
</script>

<style>
    .card-text {
    text-transform: capitalize;
    }
</style>

<div class="container-fluid bg-dark text-light p-5 text-center">
   <h1>Star Wars 101</h1>
</div>

<div class="container text-center mt-3">
    <h2>Type in a character's ID</h2>

    <form on:submit|preventDefault={getInfo}>
        <label for="ID">Character ID:</label>
        <input id="id" bind:value={uid} type="number" />
        <button type="submit">Check</button>
    </form>
    
    <div class="card bg-primary mt-3 mb-3 w-50 m-auto">
        <div class="card-header bg-dark text-light">Name: {name}</div>
            <div class="card-body bg-light">
                <p class="card-text">Gender: {gender}</p>
                <p class="card-text">Height: {height}cm</p>
                <p class="card-text">Weight: {weight}kg</p>
                <p class="card-text">Hair color: {hair_color}</p>
                <p class="card-text">Eye color: {eye_color}</p>
                <p class="card-text">Birth year: {birth_year}</p>
            </div>
        </div>
    </div>

