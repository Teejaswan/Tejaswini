<script>
  import Header from "./sections/header/Main.svelte";
  import Experience from "./sections/experience/Main.svelte";
  import Skills from "./sections/skills/Main.svelte";
  import Footer from "./sections/footer/Main.svelte";
</script>


<main>
  <div class="grain-overlay"></div>
  <Header></Header>
  <Experience></Experience>
  <Skills></Skills>
  <Footer></Footer>
</main>

<style>
  main {
    position: relative;
    padding-inline: var(--secpadinline);
    color: white;
    overflow-x: hidden;
    font-family: "Canosa";
  }
  .grain-overlay {
    opacity: 0.12;
    background-image: url(./assets/grain.gif);
    background-position: 50%;
    background-size: auto;
    position: fixed;
    pointer-events: none;
    z-index: 10000;
    top: 0%;
    bottom: 0%;
    left: 0%;
    right: 0%;
  }
</style>
