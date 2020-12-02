<template>
    <aside class="temp">
        
        <span class="temperature">
            {{ Math.round(weather.main.temp-274.15) }}°C
        </span>

        <span class="weather">
            {{ weather.weather[0].main }}
        </span>
    </aside>
</template>

<script>
    export default {
        props: [
            'weather'
        ],
    }
</script>

<style lang="scss" scoped>

.temp {
    display: flex;
    flex-direction: column;
    justify-content: center;

    margin: 2em auto;
    width: 95%;
    max-width: 300px;

    background-color: rgba(255, 255, 255, 0.25);
    box-shadow: 4px 6px 3px rgba(0, 0, 0, 0.25);
    border-radius: 20px;
}

.weather {
    color: rgb(70, 70, 70);
}

.temperature {
    font-size: 6em;
    font-weight: 800;
    text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}

.meta {
    font-size: 0.3em;
    text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
    
    background-color: #333;
    border-radius: 20px;
}

@media screen and (max-width: 593px) {
    .temperature  {
        font-size: 5em;
    }
}

</style>