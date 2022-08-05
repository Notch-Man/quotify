<script>
  export let quote, author;
</script>

<main>
  <div class="card border border-primary">
    <div class="card-body p-5">
      <h3 class="card-title lead text-center">
        <i>{quote || "Loading..."}</i>
      </h3>
      <p class="mb-0 mt-3 blockquote text-center">
        <mark>{author || "Loading..."}</mark>
      </p>
    </div>
  </div>
</main>

<style>
  .card {
    margin-right: 50px;
    margin-left: 50px;
    cursor: pointer;
    transition: 0.5s ease-in-out;
  }
  .card:hover {
    transform: scale(1.05);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.12), 0 4px 8px rgba(0, 0, 0, 0.06);
  }
  h3 {
    font-size: 25pt;
  }
  p {
    font-weight: 600;
  }
</style>
