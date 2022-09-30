<script>
	import Router from 'svelte-spa-router'
    import About from './routes/About.svelte';
    import Auth from './routes/Auth.svelte';
	import Home from './routes/Home.svelte'
    import Post from './routes/Post.svelte';
    import Posts from './routes/Posts.svelte';

	let routes = {
		'/': Home,
		'/auth': Auth,
		'/posts': Posts,
		'/about': About,
		'/post/:id': Post
	}
	//<Router {routes}/>
</script>

<main>
	<Router {routes}/>
</main>

<style>
	main {
		text-align: center;
		max-width: 100vw;
		max-height: 100vh;
		width: 100%;
		height: 100%;
		position: sticky;
	}
	:global(body){
		background-color: #16213E;
		padding: 0;
	}
	

</style>