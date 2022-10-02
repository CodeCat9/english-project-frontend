<script>
  import axios from 'axios';
  import { push } from 'svelte-spa-router';

  let email = "";
  let password = "";
  let err = "";

  function submitLogin(){
    axios.post("https://english-project-364018.ey.r.appspot.com/api/auth/local", {
      identifier: email,
      password: password
    }).then(response => {
      localStorage.setItem('token', response.data.jwt) 
      push('#/')
    }).catch(error => {
      if(error.response){
        console.log(error)
        err = error.response.data.error.details.errors[0].message;
        err = err.charAt(0).toUpperCase() + err.slice(1) + "!"
      }
    })
  }

</script>


<div>
  <form on:submit|preventDefault={submitLogin}>
    <label for="emailLogin">Email</label>
    <input type="text" id="emailLogin" name="firstname" placeholder="Email" bind:value={email} />

    <label for="passwordLogin">Password</label>
    <input 
      bind:value={password}
      type="password"
      id="passwordLogin"
      name="password"
      placeholder="Password"
    />

    {#if err.length > 0}
      <section class="error">{err}</section>
    {/if}

    <input type="submit" value="Login" />
  </form>
</div>

<style>
  .error{
      color: crimson;
    }
  input[type="text"]{
    width: 100%;
    padding: 1vw 2vw;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid #ccc;
    background-color:  #2f3b5c;
    color: #dedede;
    border-radius: 4px;
    box-sizing: border-box;
  }
  input[type="password"]{
      width: 100%;
      padding: 1vw 2vw;
      margin: 8px 0;
      display: inline-block;
      border: 1px solid #ccc;
      background-color:  #2f3b5c;
      color: #dedede;
      border-radius: 4px;
      box-sizing: border-box;
    }
  ::placeholder{
    color: #dedede;
  }

  label{
    color: #dedede;
  }

  input[type="submit"] {
    width: 100%;
    background-color: #008080;
    color: white;
    padding: 14px 20px;
    margin: 8px 0;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }

  input[type="submit"]:hover {
    background-color: #66b2b2;
  }

  div {
    border-radius: 1vw;
    background-color: #222d4d;
    padding: 20px;
  }
</style>
