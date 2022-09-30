

<div class="page">
     <!--<NavBar/>
    <div class="container">
        {#each posts as post }
            <script>
                console.log(post)
            </script>
            <PostT id={post.id} image={post.attributes.photo.data.attributes.url} description={post.attributes.description} title={post.attributes.title} author={post.attributes.author.data.attributes.username} date={post.attributes.date} />
        {/each}
    </div>-->
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