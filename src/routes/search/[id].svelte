<script context="module">
    export async function load({fetch, params}){
        const res = await fetch (
        `https://api.themoviedb.org/3/search/movie?api_key=${import.meta.env.VITE_API}&language=en-US&query=${params.id}&page=1&include_adult=false`
        );
        const data = await res.json();
        if(res.ok){
            return {
                props: {searchedMovie: data.results}
            };
        } 
    }

</script>

<script>
    import MovieCard from "../../components/MovieCard.svelte";
    export let searchedMovie;
</script>

<div class="searched-movies">
    <!-- <h2>Displaying results for:</h2> 
    <h1>{inputValue}</h1> -->
    {#each searchedMovie as  movie}
      <MovieCard {movie}  />
    {/each}
</div>

<style>
    .searched-movies{
        padding-top: 3rem;
        padding-left: 3rem;
		padding-right: 3rem;
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        grid-column-gap :1rem;
        grid-row-gap: 2rem;
        height: 15vh;
    }
</style>