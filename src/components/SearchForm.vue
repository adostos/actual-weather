<template>
    <form class="search-box" @submit.prevent="fetchWeather">
        
        <div class="what">
            Find your city or country
        </div>
        
        <input
            type="text"
            class="search-input"
            placeholder="Search..."
            v-model="query"
        />

        <p class="date">
            {{ dateBuilder() }}
        </p>
    </form>
</template>

<script>
import axios from 'axios'

    export default {
        data() {
            return {
                api_key: '01d173fa50230c4e27143afd37a8ce86',
                query: '',
            }
        },
        methods: {
            fetchWeather() {
                axios
                .get(`https://api.openweathermap.org/data/2.5/weather?q=${encodeURI(this.query)}&appid=${this.api_key}`)
                .then(response => {
                    this.$emit('name-city', response.data)
                    this.$emit('temp-val', response.data.main.temp-274.15)
                })
                .catch( error => {
                    alert('Please enter the correct city or country', error)
                })
                this.query = ''
            },
            dateBuilder() {
                let d = new Date();
                let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
                let days = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"];

                let day = days[d.getDay()];
                let date = d.getDate();
                let month = months[d.getMonth()];
                let year = d.getFullYear();

                return `${day} ${date} ${month} ${year}`
            }
        }
    }
</script>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Acme&display=swap');

* {
    font-family: 'Acme', sans-serif;
}

.search-box {
    width: 100%;
    max-width: 500px;
    margin-top: 2em;
    margin-bottom: 8px;
}

.what {
    margin-bottom: 0.5em;
    opacity: 0.8;

    color: white;
    font-size: 1.2em;
    font-style: normal;
    font-weight: normal;
    letter-spacing: 1px;
}

.search-input {
    display: block;
    width: 100%;
    padding: 0.5em;

    color: rgba(0, 0, 0, .8);
    font-size: 1.5em;

    border: none;
    outline: none;
    appearance: none;
    background: none;

    background: rgba(255, 255, 255, .5);
    border-radius: 0 20px 0 20px;
    box-shadow: 4px 6px 3px rgba(0, 0, 0, 0.25);

    transition: all .5s ease-in-out;
}

.search-input:hover, .search-input:focus {
    background: rgba(255, 255, 255, .9);
    border-radius: 20px 0 20px 0;
}

.search-input::placeholder {
    color: white;
    opacity: .9;
    
}

.search-input:focus::placeholder,
.search-input:hover::placeholder {
    transition: all .5s ease-in-out;
    color: black;
    opacity: .7;
}

.date {
    margin-top: 0.5em;
    color: white;
    opacity: 0.8;
    font-weight: normal;
    font-size: 0.8em;
    letter-spacing: 1px;
}

@media screen and (max-width: 593px) {
    .search-input {
        padding: .2em;
        border-radius: 0 10px 0 10px;
    }
}
</style>