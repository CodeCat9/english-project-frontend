<script>
    import NavBar from "../components/NavBar.svelte";
    import {onMount} from 'svelte'
    import SvelteMarkdown from 'svelte-markdown'

    let id = window.location.hash;
    id = id.split('/')[2];
    let post
    let content 
    let title
    let description
    onMount(async () => {
        post = await fetch('https://english-project-364018.ey.r.appspot.com/api/posts/' + id).then(x => x.json())
        console.log(post.data.attributes)
        content = post.data.attributes.content
        title = post.data.attributes.title
        description = post.data.attributes.description
    })
</script>

<NavBar/>
<div class="container">
    <h1>{title}</h1>
    <div>{description}</div>
    <SvelteMarkdown source={content}/>
</div>


<style>
    .container{
        background-color: #533483;
        color: #cccdcf;
        width: 80vw;
        padding: 1%;
        margin: 10%;
        align-items: center;
        text-align: left;
        word-wrap: break-word;
        white-space: normal;
    }

</style>