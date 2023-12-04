<script>
	import { getWeatherFrom } from '../services/weather';
	const weatherPromise = getWeatherFrom();
</script>

{#await weatherPromise then weather}
	<h1>{weather.conditionText}</h1>
{/await}

<h1>Renderizado</h1>
