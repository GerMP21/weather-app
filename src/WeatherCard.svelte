<script>
    export let data;
</script>

<div class="card">
    <h1>Weather in {data.name}</h1>
    <h2>
        {data.weather[0].main}
    </h2>
    <img src="icons/{data.weather[0].main}.png" alt="{data.weather[0].main}">
    <ul>
        <li>Temperature: {data.main.temp}°</li>
        <li>Humidity: {data.main.humidity}%</li>
        <li>Wind Speed: {data.wind.speed}m/s</li>
    </ul>
</div>

<style>

    .card {
        background-color: #f0f0f0;
        text-align: center;
        margin-left: 30%;
        margin-right: 30%;
        margin-bottom: 20px;
        border: 1px solid black;
        border-radius: 20px;
    }

    ul {
        text-align: left;
        list-style-type: none;
    }
</style>