<script>
  import cds from "../assests/cds.png";
  import { onMount } from "svelte";
  import { gsap } from "gsap";

  import { ScrollTrigger } from "gsap/ScrollTrigger";

  gsap.registerPlugin(ScrollTrigger);
  let imgel;
  onMount(() => {
    gsap.to(imgel, {
      scale: 1.1,
      duration: 1,
      yoyoEase: true,
      scrollTrigger: {
        trigger: imgel,
        start: "top center",
        end: "top top",
        toggleActions: "restart pause reverse resume",
        scrub: 1,
      },
    });
  });
</script>

<div class="cds">
  <div class="description">
    <span><h3>CONTINUUM DESIGN SYSTEM</h3></span>

    <p>
      A modern and beautiful that provides a set of reusable UI components,
      design guidelines, and tools for web development.
    </p>
  </div>
  <a class="img-wrap" href="https://cds-design.github.io/" target="_blank">
    <img src={cds} bind:this={imgel} alt="cds" class="red-img" />
  </a>
</div>

<style>
  .cds {
    display: grid;
    grid-template-columns: 1fr 50%;
    justify-items: end;
    gap: 1rem;
    margin-block-end: 2rem;
  }
  .cds img {
    width: 100%;
    margin-inline-end: calc(0px - var(--secpadinline));
    aspect-ratio: 16/9;
    object-fit: cover;
  }
  .description {
    display: flex;
    flex-direction: column;
    gap: 2rem;
  }
  h3 {
    font-family: "Banigar";
    font-size: 4rem;
  }

  @media screen and (max-width: 700px) {
    h3 {
      font-size: clamp(0.75rem, 2rem, 3rem);
    }
  }
  span {
    overflow: hidden;
  }
  p {
    font-size: 1.25rem;
  }
  .img-wrap {
    width: 100%;
    overflow: hidden;
    aspect-ratio: 16/9;
  }
</style>
