<template>
    <div class="other">
        <span>
            <strong>Perception</strong>
            <br />
            {{ Math.round(weather.main.feels_like-274.15) }} °C
        </span>
        <span>
            <strong>Wind</strong>
            <br />
            {{ weather.wind.speed }}m/s
        </span>
        <span>
            <strong>Cloudiness</strong>
            <br />
            {{ weather.clouds.all }}%
        </span>
        <span>
            <strong>Humidity</strong>
            <br />
            {{ weather.main.humidity }}%
        </span>               
    </div>
</template>

<script>
    export default {
        props: [
            'weather'
        ],
    }
</script>

<style lang="scss" scoped>
.other {
    display: flex;
    width: 90%;
    max-width: 500px;
    padding: 0.5em;
    color: white;
    font-size: 1em;
    font-weight: 500;

    background-color: rgba(255, 255, 255, 0.25);
    border-radius: .5em;
    margin-top: 0.5em;

    box-shadow: 4px 6px 3px rgba(0, 0, 0, 0.25);
}

span {
    opacity: 0.8;
    font-weight: lighter;
}

strong {
    opacity: 1;
}
</style>