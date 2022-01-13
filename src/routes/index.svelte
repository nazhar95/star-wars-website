<script>
    let location="";
    let weatherTemperature="";
    let weatherDescription="";

    async function getWeather() {
        fetch('https://goweather.herokuapp.com/weather/' + location)
            .then((response) => response.json())
            .then((data) => {
                weatherTemperature = data.temperature; // Path for temperature
                weatherDescription = data.description; // Path for description
            });
    }

</script>
<div class="jumbotron">
    <h1 class="display-3">Hello, world!</h1>
    <p class="lead">This is a simple hero unit, a simple jumbotron-style component for
                    calling extra attention to featured content or information.</p>
    <hr class="my-2">
    <p>It uses utility classes for typography and
       spacing to space content out within the larger container.</p>
    <p class="lead">
      <a class="btn btn-primary btn-lg" href="#!" role="button">Some action</a>
    </p>
  </div>
  
<h1>Weather App</h1>

<form on:submit|preventDefault={getWeather}>
    <label for="location">Location:</label>
    <input id="location" bind:value={location} type="text" />
    <button type="submit">Check</button>
</form>

<p>Temperature: {weatherTemperature}</p>
<p>Description: {weatherDescription}</p>
