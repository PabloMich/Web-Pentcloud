<script lang="ts" context="module">
  import Counter from "./routes/Counter.svelte";
  import Navbar from "./routes/Navbar.svelte";
  import Router from "svelte-spa-router";
  import Inicio from "./routes/Inicio.svelte";
  import Articulos from "./routes/Articulos.svelte";
  import ArtAutor from "./routes/ArtAutor.svelte";
  import ArtCategoria from "./routes/ArtCategoria.svelte";

  let routes = {
    "/": Inicio,
    "/articulos": Articulos,
    "/articuloAutor": ArtAutor,
    "/articuloCategoria": ArtCategoria,
  };

  import { request, gql } from "graphql-request";

  const query = gql`
    {
      countries {
        name
        emoji
      }
    }
  `;
  request("https://countries.trevorblades.com/", query).then((data) =>
    console.log(data)
  );
</script>

<main>
  <div class=" pb-6 sm:pb-8 lg:pb-12">
    <div class="max-w-screen-2xl px-4 md:px-8 mx-auto">
      <Navbar />
      <Router {routes} />
    </div>
  </div>
</main>

<style global lang="postcss">
  @tailwind base;
  @tailwind components;
  @tailwind utilities;
</style>
