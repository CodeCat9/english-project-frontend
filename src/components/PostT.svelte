
<script>

    import database_url from '../App.svelte'

    export let title;
    export let author;
    export let date;
    export let image;
    export let description;
    export let id;


</script>


<div class="container">
    <a href="#/post/{id}">
        <img src="{database_url}{image}" alt="">
        <div class="text">
            <h3 class="title">{title}</h3>
            <p class="description">{description}</p>
        <div class="bottom">
            <p class="author">{author}</p>
            <p class="date">{date}</p>
        </div>
    </div>
    </a>
    
    
</div>

<style>
    a{
        text-decoration: none;
        color: #cccdcf;
    }
    .top{
        display: flex;
        align-items: left;
        max-width: 23vw;
        max-height: 13vh;
        flex-direction: column;
    }
    .bottom{
        max-width: 23vw;
        height: 12vh;
        position: relative;
    }
    .author{
        position: absolute;
        left: 1vw;
        bottom: 3vh;
    }
    .date{
        position: absolute;
        right: 1vw;
        bottom: 3vh;
    }

    .description{
        max-width: 23vw;
    }
    .title{
        max-width: 23vw;
    }
    img{
        width:25vw;
        height: 25vh;
    }
    .text{
        align-items: center;
        width: 25vw;
        height: 25vh;
        word-wrap: break-word;
    }
    .container{
        width: 25vw;
        height: 50vh;
        background-color: #256D85;
        border-color: #0F3460;
        border-width: 3%;
        border-style: solid;
        align-items: center;
    }
</style>