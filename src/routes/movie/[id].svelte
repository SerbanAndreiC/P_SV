<script context="module">
    
        export async function load({ fetch, params }) {
            const res = await fetch(
                `https://api.themoviedb.org/3/movie/${params.id}?api_key=${import.meta.env.VITE_API}&language=en-US&page=1`
            );
            const movieDetail = await res.json();
            if (res.ok) {
                return {
                    props: { movieDetail }
                };
            }
        }
    </script>
    
    <script>
        export let movieDetail;
        import {fly} from 'svelte/transition';
    </script>
    
    <div class="movie-details-page" in:fly={{y: 50, duration:500, delay:500}} out:fly={{ duration:500}}>
        <div class="movie-details">
            <div class="image-container">
                <img
                    src={'http://image.tmdb.org/t/p/original' + movieDetail.backdrop_path}
                    alt={movieDetail.title}
                />
                <div class="holder">
                    <span class="align">Release date: <p class="align2">{movieDetail.release_date}</p></span>
                    <span class="align">Budget:$  <p class="align2">{movieDetail.budget} </p> </span> 
                    <span class="align">Rating: <p class="align2">{movieDetail.vote_average}</p> </span>  
                    <span class="align">Runtime: <p class="align2">{movieDetail.runtime}</p> </span>
                </div>
            </div>
            
                
            <div class="descriprion">
                <h2>{movieDetail.title}</h2>
                <p class="overview">{movieDetail.overview}</p>
            </div>
        </div>
        
    </div>
    
    <style>
        .movie-details-page{
            padding-top:3rem;
            height: auto;
            padding-left: 5%;
            padding-right: 5%;
        }
        h2 {
            padding: 0 2rem;
        }
        p {
            font-weight: normal;
            width: 90vw;
        }
        .image-container {
            width: 90vw;
            display: flex;
            align-items: flex-start;
            justify-content: center;
            
        }
        img {
            width: 100%;
            height: 73vh;
            object-fit: cover;
            border-radius: 1rem;
        }
       
        .movie-details {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .align {
            display:inline-flex;
            line-height: 0.9rem;
            width: 12rem;
            font-weight: bold;
            font-size: 0.9rem;
            padding: 1rem 0rem;
        }
        .align2{
            line-height: 0.9rem;
            font-weight: normal;
            font-size: 0.9rem;
            padding: 0rem 0.6rem;
            margin:0;
        }
        .holder{
            display: flex;
            flex-wrap: wrap;
            width: 12rem;
            padding-left: 1rem;
            
        }
        @media screen and (max-width: 1200px) {
            .image-container {
            width: 80vw;
            display: flex;
            flex-direction: column;
            align-items: flex-start;
            justify-content: center;
            
            }
            .holder{
            display:flex;
            flex-direction: row;
            flex-wrap: wrap;	
            }
    
        }
    </style>
    