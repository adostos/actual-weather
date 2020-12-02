/* eslint-disable vue/no-parsing-error */
<template>
    <div id="app">
        <main :class="{cold: temperature < 1, hot: temperature > 20}">

            <h1>actual weather</h1>

            <search-form @name-city="weather = $event" @temp-val="temperature = $event" />
            
            <article v-if="typeof weather.main !='undefined'">
                <city-name :weather="weather" />

                <temperature-info :weather="weather" />

                <other-info :weather="weather" />
            </article>
        </main>
    </div>
</template>

<script>
import SearchForm from './components/SearchForm';
import CityName from './components/CityName';
import TemperatureInfo from './components/TemperatureInfo';
import OtherInfo from './components/OtherInfo';

export default {
    components: { SearchForm, CityName, TemperatureInfo, OtherInfo },
    name: 'App',
    data() {
        return {
            weather: {},
            temperature: ''
        }
    },
}
</script>

<style>
@import './main.scss';

#app {
    background-color: rgb(18, 188, 255);
}

main {
    min-height: 100vh;
    padding: 1em;
    background-image: linear-gradient(to bottom, rgba(128, 55, 55, 0), rgba(0, 146, 204, 0.76));
}

.cold {
    background-image: linear-gradient(to bottom, rgba(128, 55, 55, 0), rgba(231, 230, 230, 0.8));
}
.hot {
    background-image: linear-gradient(to bottom, rgba(128, 55, 55, 0), rgba(255, 0, 0, 0.815));
}

h1 {
    text-transform: uppercase;
    color: whitesmoke;
    margin-top: 1em;
    font-weight: normal;
    letter-spacing: 3px;
    font-size: 3em;
}

@media screen and (max-width: 593px) {
    h1 {
        font-size: 2em;
    }

}

</style>
