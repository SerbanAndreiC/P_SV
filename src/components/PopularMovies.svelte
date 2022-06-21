<script>
    export let popular;
    import MovieCard from "./MovieCard.svelte";

</script>

<div class="popular-movies">
    {#each popular as movie}
        <MovieCard {movie}/>
    {/each }
</div>

<style>
   
    .popular-movies{
        padding-top: 3.5rem;
        padding-left: 3rem;
        padding-right: 3rem;
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        grid-column-gap :1rem;
        grid-row-gap: 2rem;
    }
</style>