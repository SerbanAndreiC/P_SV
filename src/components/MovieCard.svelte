<script>
    export let movie;
</script>

<div class="movie-card">
    <a sveltekit:noscroll href={'/movie/'+ movie.id}>
        <img src={'http://image.tmdb.org/t/p/w500' + movie.poster_path} alt={movie.title}/>
    </a>
    <div class="description">
        <h2>{movie.title}</h2>
        <p>{movie.release_date}</p>
    </div>
</div>




<style>
    img {
        width: 100%;
        height: 70vh;
        object-fit:cover;
        border-radius: 0.9rem;
        margin-bottom: 1rem;
    }
    h2{
        font-size: 0.9rem;
    }
    p{
        font-size: 0.7 rem;
    }
    .movie-card{
        padding-top: 5rem;
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        padding: 0.2rem;
    }
</style>