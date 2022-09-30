<script>
    import NavBar from "../components/NavBar.svelte";
</script>

<div>
    <NavBar/>
    <div class="parent">
        <div class="child image">
            <img src="https://images7.alphacoders.com/116/thumb-1920-1163218.png" alt="" class="feynman">
        </div>

        <div class="child text">
            <div class="heading">
                <h1>Welcome to my physics blog!</h1>
                <h1>Here, i post what i learn trough</h1>
                <h1>my physics researches.</h1>
                <h1>Come and join me in this journey </h1>
                <h1>of defining the universe...</h1>
            </div>
            
        </div>
    </div>
    
</div>

<style>
    .child{
        position: absolute;
        top: 10vh;
    }

    .parent{
        position: relative;
    }

    .heading{
        text-align: left;
    }

    .image{
        top: 10vh;
        left: 5vw;
    }

    .text{
        top: 20vh;
        left: 7vw;
        color: #cccdcf;
    }
    .feynman{
        width: 90vw;
        height: 90vh;   
    }
</style>