<template>
    <div class="" id="tvDetail" :style="backgroundImage">
        <div class="row">
            <div class="col s12 m4" id="detailPoster">
                <img :src="imgUrl">
            </div>
            <div class="col s12 m8" id="detailInfo">
                <h4 class="center">{{detail.name}}</h4>
                <p>Overview</p>
                <p class="light">{{detail.overview}}</p>
                <p>Homepage</p>
                <a class="light" :href="detail.homepage">Link</a>
                <p>Original Language</p>
                <p class="light">{{detail.original_language}}</p>
                <p>Episodes</p>
                <p class="light">{{detail.number_of_episodes}}</p>
                <p>Seasons</p>
                <p class="light">{{detail.number_of_seasons}}</p>
                <button class="btn" @click.prevent="emptyDetail">Back</button>
            </div>
        </div>
    </div>
    
</template>

<script>
export default {
    name: 'tvDetail',
    props: ['detail'],
    data() {
        return {
            imgUrl: `https://image.tmdb.org/t/p/w500${this.detail.poster_path}`,
            backdropPath: `https://image.tmdb.org/t/p/w500${this.detail.backdrop_path}`
        }
    },
    methods: {
        emptyDetail() {
            this.$emit('emptyDetail')
        }
    },
    computed: {
        backgroundImage(){
            return {
                "background-image": this.backdropPath
            }
        }
    }
}
</script>

<style scoped>
img {
    height: 550px;
}
</style>