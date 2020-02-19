<template>
 <transition name="fade">
    <div class="movie-wrapper" :style="styles">
        <div class="movie-info">
        <h1>{{ movie.title}}</h1>
        <h3>Release Date:{{ movie.release_date}}</h3>
        <p>
            {{ movie.overview}}

        </p>
        </div>
    </div>
 </transition>
</template>

<script>
const  BACKDROP_PATH = " http://image.tmdb.org/t/p/w1280";
    export default {
            data(){
            return {
                movie: {}
            }
        },
        created: function() {
            this.fetchData();
        },
       computed: {
            styles() {
                return {
                    background: `url(${BACKDROP_PATH}/${this.movie.backdrop_path})  no-repeat`
   
                    

                }
            }
        }, 
        methods:{
            fetchData: async function(){
                try {
                    const res= await fetch(
                        `https://api.themoviedb.org/3/movie/${this.$route.params.id}?api_key=18d437f77122a90a5844237e51d0551e`);
                    const movie = await res.json();
                    this.movie = movie;
                } catch(e){
                   
                }
            }
        },
    }
</script>

<style lang="scss" scoped>
.movie-wrapper{
    position: relative; 
    padding-top: 50vh;
    background-size: cover;
 
  
}
.movie-info{
     background: red;
     color: #222;
     padding: 2rem 10%;
   

}

 .fade-enter-active,
 .fade-leave-active{
     transition: all 0.3s ease;
    }
 .fade-enter,
 .fade-leave-to{
     opacity: 0;
     transform: translateX(100);
    }

</style>