<script>
  function logout(){
    localStorage.removeItem('token')
  }
  //on:click={logout}
</script>

<div class='wrapper'>
    <div class='container'>
        <ul>
            <li><a href="#/">Home</a></li>
            <li><a href="#/about">About</a></li>
            <li><a href="#/posts">Posts</a></li>
            {#if localStorage.getItem('token')}
                <li><a href="#/auth" on:click={logout}>Logout</a></li>
            {:else}
                <li><a href="#/auth">Login/Register</a></li>
            {/if}
            
        </ul>
        

    </div>
</div>

<style>
    a{
        color: #cccdcf;
    }
    ul{
        display: flex;
        list-style: none;
        justify-content: space-around;
        margin-top: 2vh;
    }

    li{
        margin-right: 5vw;
        
    }

    button{
        background-color: #0F3460;
        border-style: none;
        color: #cccdcf;
        width: 25px;
        height: 3vh;
        margin-right: 1vw;
        margin-bottom: 5vh;
    }

    .container{
        justify-content: space-around;
        display: flex;
        align-items: center;
        font-size: 25px;
    }

    .wrapper{
        max-width: 100%;
        max-height: 100%;
        width: 100vw;
        height: 10vh;
        background-color: #0F3460;
        position: fixed;
        top: 0;
    }
</style>