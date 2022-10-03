<script>
  import NavBar from "../components/NavBar.svelte";
  import { onMount } from "svelte";
  import SvelteMarkdown from "svelte-markdown";
  import { fade, scale } from "svelte/transition";
  import Comment from "../components/Comment.svelte";
  import axios from "axios";
  import jwt_decode from "jwt-decode";

  let id = window.location.hash;
  id = id.split("/")[2];
  let post;
  let content;
  let title;
  let description;
  let comments = [];

  let formUsername;
  let formContent;
  let formDate;

  onMount(async () => {
    post = await fetch(
      "https://english-project-364018.ey.r.appspot.com/api/posts/" +
        id +
        "?populate=*"
    ).then((x) => x.json());
    let decoded = jwt_decode(localStorage.getItem("token"));
    axios
      .get(
        "https://english-project-364018.ey.r.appspot.com/api/users/" +
          decoded.id
      )
      .then((response) => {
        formUsername = response.data.username;
      });
    comments = post.data.attributes.comments.data;
    content = post.data.attributes.content;
    title = post.data.attributes.title;
    description = post.data.attributes.description;
  });

  function comment() {
    if (formContent) {
      formDate = new Date(Date.now()).toISOString();
      comments = [
        ...comments,
        {
          attributes: {
            content: formContent,
            username: formUsername,
            date: formDate,
          },
        },
      ];
      axios.post(
        "https://english-project-364018.ey.r.appspot.com/api/comments",
        {
          headers: {
            Authorization: "Bearer" + localStorage.getItem("token"),
          },
          data: {
            content: formContent,
            username: formUsername,
            date: formDate,
            post: id
          },
        }
      );
    }
  }
</script>

<div class="page">
  <NavBar />
  <div class="container" in:scale out:fade>
    <h1>{title}</h1>
    <div>{description}</div>
    <SvelteMarkdown source={content} />
  </div>
  {#if localStorage.getItem("token")}
    <div class="commentForm">
      <textarea
        bind:value={formContent}
        name="comment"
        id="comment"
        placeholder="Enter your comment..."
        cols="30"
        rows="10"
      />
      <button class="submitButton" on:click={comment}>Comment</button>
    </div>
  {:else}
    <p>Log in to make comment!</p>
  {/if}
  {#each comments as comment}
    <Comment
      username={comment.attributes.username}
      content={comment.attributes.content}
      date={comment.attributes.date}
    />
  {/each}
</div>

<style>
  ::placeholder {
    color: #cccdcf;
  }
  .submitButton {
    width: 10vw;
    height: 10vh;
    background-color: #008080;
    color: #cccdcf;
    margin-left: 40vw;
  }
  textarea {
    border-radius: 3vw;
    padding: 3vw;
    color: #cccdcf;
    background-color: #222d4d;
    width: 50vw;
    height: 30vh;
  }
  .commentForm {
    margin-top: 5vh;
    width: 60vw;
    height: 50vh;
    margin-left: 20vw;
  }
  .container {
    border-radius: 3vw;
    background-color: #533483;
    color: #cccdcf;
    width: 82vw;
    padding: 4vw;
    margin-top: 15vh;
    margin-right: 5vw;
    margin-left: 5vw;
    align-items: center;
    text-align: left;
    word-wrap: break-word;
    white-space: normal;
  }
  p {
    color: #cccdcf;
  }
</style>
