<div>
  <form action="/action_page.php">
    <label for="email">Email</label>
    <input type="text" id="email" name="firstname" placeholder="Your Email" />

    <label for="password">Password</label>
    <input
      type="text"
      id="password"
      name="password"
      placeholder="Your password"
    />

    <input type="submit" value="Login" />
  </form>
</div>

<style>
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
