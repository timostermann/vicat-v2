<script lang="ts">
  import { Router, Route } from "svelte-navigator";
  import Navigation from "./components/Navigation.svelte";
  import Team from "./pages/Team.svelte";
  import Faq from "./pages/Faq.svelte";
  import PreSale from "./pages/Presale.svelte";
  import Home from "./pages/Home.svelte";
  import Nft from "./pages/Nft.svelte";
  import Icon from "./assets/images/vicat_small.svg";
</script>

<svelte:head>
  <link rel="icon" href={Icon} />
</svelte:head>
<main>
  <Router>
    <Navigation />
    <Route path="/" component={Home} />
    <Route path="team" component={Team} />
    <Route path="faq" component={Faq} />
    <Route path="presale" component={PreSale} />
    <Route path="nft" component={Nft} />
  </Router>
</main>

<style>
  @import "./App.css";
</style>
