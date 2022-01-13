<script>
    let name="";
    let planet="";
    let height="";
    

    async function getWeather() {
        fetch('https://goweather.herokuapp.com/weather/' + location)
            .then((response) => response.json())
            .then((data) => {
                weatherTemperature = data.temperature; // Path for temperature
                weatherDescription = data.description; // Path for description
            });
    }

</script>

<div class="container-fluid bg-dark text-light p-5 text-center">
   <h1>Star Wars 101</h1>
</div>

<div class="container text-center mt-3">
    <h2>Type in a character's name</h2>

    <form on:submit|preventDefault={getWeather}>
        <label for="location">Location:</label>
        <input id="location" bind:value={location} type="text" />
        <button type="submit">Check</button>
    </form>
    
    <p>Temperature: {weatherTemperature}</p>
    <p>Description: {weatherDescription}</p>
</div>

