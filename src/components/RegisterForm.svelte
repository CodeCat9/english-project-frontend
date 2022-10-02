<script>
  import axios from "axios";
  import { push } from "svelte-spa-router";



  let username = "";
  let email = "";
  let password = "";
  let passwordConfirm = "";
  let isEqual = true;

  let err = "";
  let validity = "";
  let emailValidity = "";

  const validateEmail = () => {
    return email
    .toLowerCase()
    .match(
      /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
    );
  };

  function checkEqual(){
    isEqual = password === passwordConfirm;
    if(isEqual){
      validity = "✓"
    } else {
      validity = "✖"
    }
  }

  function isEmailValid(){
    if(validateEmail()){
      emailValidity = "✓"
    } else {
      emailValidity = "✖"
    }
  }

  function submitRegister(){
    axios.post("https://english-project-364018.ey.r.appspot.com/api/auth/local/register", {
      username: username,
      password: password,
      email: email
    }).then(res => {
      localStorage.setItem('token', res.data.jwt)
      push('/')
    }).catch((error) =>{
      if(error.response){
        err = error.response.data.error.details.errors[0].message
        err = err.charAt(0).toUpperCase() + err.slice(1) + "!"
      }
    })
  }

</script>


<div>
    <form on:submit|preventDefault={submitRegister}>
        <label for="username">Username</label>
      <input bind:value={username} type="text" id="username" name="username" placeholder="Username" />
      
      <label for="email">Email {emailValidity}</label>
      <input on:change={isEmailValid} bind:value={email} type="text" id="email" name="email" placeholder="Email" />
  
      <label for="password">Password</label>
      <input
        bind:value={password}
        on:change={checkEqual}
        type="password"
        id="password"
        name="password"
        placeholder="Password"
      />
      
      <label for="password">Confirm Password {validity}</label>
      <input
        bind:value={passwordConfirm}
        on:change={checkEqual}
        type="password"
        id="confirm"
        name="confirm"
        placeholder="Confirm Password"
      />

      {#if err.length > 0}
        <section class="error">{err}</section>
      {/if}
      
      <input type="submit" value="Register" />
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
  