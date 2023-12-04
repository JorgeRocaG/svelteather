<script>
	const url = 'https://weatherapi-com.p.rapidapi.com/current.json?q=53.1%2C-0.13';
	const options = {
		method: 'GET',
		headers: {
			'X-RapidAPI-Key': 'e437ee0664msh6ca03a4b5d87dedp1d535fjsn41c22e771aa7',
			'X-RapidAPI-Host': 'weatherapi-com.p.rapidapi.com'
		}
	};

	const weatherPromise = fetch(url, options)
		.then((response) => response.json())
		.then((data) => {
			const { location, current } = response;
			const { country, localtime, name } = location;
			const { condition, humidity, feelslike_c, is_day, temp_c, wind_kph, wind_dir } = current;
			const { code, text } = condition;

			return {
				conditionCode: code,
				conditionText: text,
				country,
				localtime,
				name,
				humidity,
				isDay: is_day,
				feelsLike: feelslike_c,
				temperature: temp_c,
				windSpeed: wind_kph,
				windDir: wind_dir
			};
		})
		.catch((err) => console.log(err));
</script>

{#await weatherPromise then weather}
  <h1>{weather.conditionText}</h1>
{/await}

<h1>Renderizado</h1>
