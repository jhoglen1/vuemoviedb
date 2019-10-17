<template>
 <ul>
   <li v-for='movie in movies'>
       <movie :movie="movie"/>
       </li>  
 </ul>
</template>

<script>
    import Movie from './Movie.vue';
    export default {
        name: 'MoviesList',
        data(){
            return {
                movies: []
            }
        },
        beforeCreate(){
            console.log('before create')
        },
        created: function() {
            console.log('created')
            this.fetchData();
        },
        beforeMount(){
            console.log('before mount')
        },
        mounted(){
            console.log('mounted')
        },
        beforeUpdate(){
            console.log('before update')
        },
        updated(){
            console.log('updated')
        },
        methods:{
            fetchData: async function(){
                try {
                    const res= await fetch(
                        'https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=18d437f77122a90a5844237e51d0551e');
                    const movies = await res.json();
                    this.movies = movies.results;
                } catch(e){
                    console.log(e)
                }
            }
        },
        components: {
            Movie
        }
    };
</script>

<style lang="scss" scoped>
ul{
    display: grid;
    list-style: none;
    padding: 1rem;
    margin: 0;
    grid-row-gap:  1rem;
    grid-template-columns: repeat(2, 1fr);
}
@media only screen and (min-width : 767px) {
    ul{
    display: grid;
    list-style: none;
    padding: 1rem;
    margin: 0;
    grid-row-gap:  1rem;
    grid-template-columns: repeat(6, 1fr);
}
}

</style>