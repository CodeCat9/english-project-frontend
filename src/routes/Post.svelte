<script>
  import NavBar from "../components/NavBar.svelte";
  import { onMount } from "svelte";
  import SvelteMarkdown from "svelte-markdown";
  import { fade, scale } from "svelte/transition";
  import Comment from '../components/Comment.svelte'

  let id = window.location.hash;
  id = id.split("/")[2];
  let post;
  let content;
  let title;
  let description;
  let comments = []
  onMount(async () => {
    post = await fetch(
      "https://english-project-364018.ey.r.appspot.com/api/posts/" + id + "?populate=*"
    ).then((x) => x.json());
    comments = post.data.attributes.comments.data
    content = post.data.attributes.content;
    title = post.data.attributes.title;
    description = post.data.attributes.description;
  });
</script>

<div class="page">
  <NavBar />
  <div class="container" in:scale out:fade>
    <h1>{title}</h1>
    <div>{description}</div>
    <SvelteMarkdown source={content} />
  </div>
  {#if localStorage.getItem("token")}
    <p>You are logged in</p>
  {:else}
    <p>Log in to make comment!</p>
  {/if}
  {#each comments as comment}
    <Comment username={comment.attributes.username} content={comment.attributes.content} date={comment.attributes.date} />
  {/each}
  
</div>

<style>
  .container {
    border-radius: 3vw;
    background-color: #533483;
    color: #cccdcf;
    max-width: 82vw;
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
