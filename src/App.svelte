<script>
	import Geolocation from "svelte-geolocation";
	import WeatherCard from "./WeatherCard.svelte";
	let coords = [];
	
	const fetchOpenWeather = async (lat, lon) => {
		const response = await fetch(`https://api.openweathermap.org/data/2.5/weather?lat=${lat}&lon=${lon}&units=metric&appid=${OPEN_WEATHER_API_KEY}`);
		const data = response.json();
		return data;
	}
</script>

<Geolocation getPosition bind:coords />

<header>
	Svelte weather-app
</header>

{#await fetchOpenWeather(coords[0], coords[1])}
	<p>
		Waiting for weather information...
	</p>
{:then data}
	<WeatherCard data={data} />
{:catch error}
	<p>
		Error: {error}
	</p>
{/await}

<style>
	header  {
		font-size: 2em;
		text-align: center;
		margin-bottom: 1em;
	}
</style>