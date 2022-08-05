<script>
  import { onMount } from "svelte";
  import "https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/js/bootstrap.bundle.min.js";
  import QuoteCard from "./lib/QuoteCard.svelte";
  import axios from "axios";
  import gradient from "random-gradient";

  let quote, bgradient;
  let isLoading = false;
  let endpoint = "https://api.quotable.io/random";

  async function getQuote() {
    isLoading = true;
    const res = await axios.get(endpoint);
    bgradient = gradient(crypto.randomUUID());
    quote = res.data;
    isLoading = false;
  }

  onMount(() => {
    getQuote();
  });
  $: console.log(quote, bgradient);
</script>

<main>
  <link
    href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/css/bootstrap.min.css"
    rel="stylesheet"
    integrity="sha384-gH2yIJqKdNHPEq0n4Mqa/HGKIhSkIHeL5AyhkYV8i59U5AR6csBvApHHNl/vI1Bx"
    crossorigin="anonymous"
  />
  <link
    rel="stylesheet"
    href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.9.1/font/bootstrap-icons.css"
  />

  <div class="content bg" style="background: {bgradient}">
    <QuoteCard quote={quote?.content} author={quote?.author} />

    <button
      class="btn btn-primary"
      disabled={isLoading}
      on:click={() => {
        getQuote();
      }}>Regenerate <i class="bi bi-arrow-clockwise" /></button
    >
  </div>
</main>

<style>
  .content {
    display: flex;
    justify-content: center;
    align-items: center;
    /* margin-top: 100px; */
    width: 100%;
    height: 100vh;
    transition: 0.5s ease-in-out;

    position: absolute;
    flex-direction: column;
    gap: 15px;
  }
  .bg {
    background: #159957;
    background: -webkit-linear-gradient(
      to right,
      #155799,
      #159957
    ); /* Chrome 10-25, Safari 5.1-6 */
    background: linear-gradient(to right, #155799, #159957);
  }
</style>
