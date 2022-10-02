<script>
    import LoginForm from "../components/LoginForm.svelte";
    import NavBar from "../components/NavBar.svelte";
  import RegisterForm from "../components/RegisterForm.svelte";
</script>


<div class="page">
    <NavBar/>
    <div class="loginBlock">
        <LoginForm/>
    </div>
    <div class="registerBlock">
        <RegisterForm/>
    </div>
</div>

<style>
    .page{
        display:grid;
        grid-template-columns: 5vw 40vw 10vw 40vw 5vw;
        margin-top: 20vh;
    }
    .loginBlock{
        grid-column: 2;
    }
    .registerBlock{
        grid-column: 4;
    }
</style>