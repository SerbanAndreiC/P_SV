<script>
	import Nav from '../components/Nav.svelte';
	import SearchMovie from '../components/SearchMovie.svelte';
</script>

<svelte>
	<title>Movie DB</title>
</svelte>
<div class="navbar">
	<Nav />
	<SearchMovie />
</div>

<slot />

<style>
    *{
        margin: 0;
        box-sizing: border-box;
    }
    .navbar{
        transform: translateY(-.5rem);
        padding-left: 3rem;
        padding-right: 3rem;
        position: fixed;
        display: flex;
        align-items: center;
        height: 3rem;
        background: white;
        opacity: 1;
        width: 100vw;
    }

</style>
