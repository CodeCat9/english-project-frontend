<script>
    import NavBar from "../components/NavBar.svelte";
    import axios from 'axios'
    import PostT from '../components/PostT.svelte'
    import { onMount } from 'svelte'
    //import database_url from '../App.svelte'

    let posts = []

    /*async function getPosts(url){
        const res = await fetch(url)
        const data = res
        console.log(data)
        return data;
    }*/


    onMount(() =>{
        axios.get("https://english-project-364018.ey.r.appspot.com/api/posts?populate=*").then(res =>{
            posts = res.data.data
            console.log(posts)
        })
    })

</script>

<div class="page">
    <NavBar/>
    <div class="container">
        {#await posts}
            <p>Loading...</p>
        {:then posts}
            {#each posts as post}
                <PostT id={post.id} date={post.attributes.date} description={post.attributes.description} title={post.attributes.title} 
                author={post.attributes.author.data.attributes.username} image={post.attributes.photo.data.attributes.url}/>
            {/each}
        {/await}
    </div>
</div>

<style>
    .container{
        color: #cccdcf;
        justify-content: space-around;
        display: grid;
        grid-template-rows: repeat(5, 50vh);
        grid-template-columns: 25vw 25vw 25vw;
        row-gap: 10vh;
        padding-left: 7vw;
        padding-top: 10vh;
        width: 85vw;
        min-height: 50vh;

    }

</style>