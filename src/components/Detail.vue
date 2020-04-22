<template>
    <div id="detail" v-if="movie" >
        <movie-item v-bind:movie="movie">
            <div class="movie-details">
                <p class="movie-genre">{{movie.Genre}}</p>
                <p class="movie-plot">{{movie.plot}}</p>
                <table>
                    <tr><td>Released Date: </td><td>{{movie.Released}}</td></tr>
                    <tr><td>Running Time: </td><td>{{movie.Runtime}}</td></tr>
                    <tr><td>Director: </td><td>{{movie.Director}}</td></tr>
                    <tr><td>Cast: </td><td>{{movie.Actors}}</td></tr>
                    <tr><td>Plot: </td><td>{{movie.Plot}}</td></tr>
                </table>
            </div>
        </movie-item>
        <div class="home">
            <router-link v-bind:to="{name: 'home'}">Back to: </router-link>
        </div>
    </div>

</template>

<script>
    import MovieItem from "./MovieItem.vue";
    export default {
        components: {MovieItem},
        props: ['movies'],
        computed: {
            movie() {
                let movie =  this.movies.find(movie => movie.id === this.$route.params.id);
                return movie ? movie.movie : null;
            }
        },
        name: "Detail",
        components:{
            MovieItem
        }

    }
</script>

