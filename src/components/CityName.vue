<template>
    <article class="location">

        {{ weather.name }}

        <span class="country">
            ({{ weather.sys.country }})
        </span>

        <div class="coor">
            {{ weather.coord.lat }}N
            {{ weather.coord.lon }}E
        </div>
    </article>
</template>

<script>
    export default {
        props: [
            'weather'
        ],
        
    }
</script>

<style lang="scss" scoped>
.location {
    font-size: 3em;
    font-weight: 700;
    text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
    margin: 2em;
    letter-spacing: 2px;
}

.country {
    margin-left: -10px;
    font-size: 0.5em;
    letter-spacing: 0;
    font-weight: normal;
    opacity: 0.8;
}

.coor{
    opacity: .6;
    font-weight: normal;
    font-size: .3em;
    letter-spacing: 0;
}

@media screen and (max-width: 593px) {
    .location {
        font-size: 2.5em;
        margin: 1.5em;
    }
    .country {
        font-size: 0.5em;
    }

}
</style>