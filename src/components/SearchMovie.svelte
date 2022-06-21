<script>
    let inputValue='';
    let active = false;
    import {goto} from '$app/navigation';
    import {fly} from 'svelte/transition';

    function cancelInactive() {
        if (inputValue) {
            active=true;
        } else {
            active=false;
        }
    }

    function submitSearch() {
        goto('/search/' + inputValue)
    }
</script>



<form class="search" on:submit|preventDefault={submitSearch}>
    {#if !active}
        <label for="search_movie" in:fly={{y:-10, duration:500}} out:fly={{y:-10, duration:500}}>Search Movie</label>
    {/if}
    
    <input
        on:blur={cancelInactive} 
        on:focus={()=> (active=true)} 
        bind:value={inputValue} 
        name="search_movie"
        type="text" 
        class= {active ? 'selected' : ''}/>
    {#if inputValue}    
         <button in:fly={{x:0, duration:500}} out:fly={{x:0, duration:500}}>Search</button>
    {/if}
</form>





<style>
    .search{
        position: relative;
        width: 200px;
        margin: 0.2rem;
        margin-left: calc(100vw - 410px);
    }
    input{
        width: 100%;
        border: none;
        outline: none;
        color: white;
        padding: 0.2rem 0rem;
        transition: background 0.75s ease-out;
        font-weight: bold;
        background: white;
        border:1px solid rebeccapurple;
        border-radius: 10px;
        padding: 0.5rem;
    }
    button {
        font-size: 0.8rem;
        opacity: 0.8;
        padding: 0 0.5rem;
        background: rebeccapurple;
        color: white;
        font-weight: bold;
        border: none;
        position: absolute;
        bottom: 50%;
        right: 0;
        transform: translate(30%, 50%);
        height: 100%;
        border-top-right-radius: 10px;
        border-bottom-right-radius: 10px;
        cursor: pointer;
    }
    label{
        position: absolute;
        font-size: 0.8rem;
        top: 50%;
        left: 0;
        transform: translate(0, -50%);
        pointer-events: none;
        color: rebeccapurple;;
        padding: 0 1rem;
    }
    .selected{
        background: rgb(50, 50, 50);
    }

</style>