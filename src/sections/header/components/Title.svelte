<script>
    import { gsap } from "gsap";

    import { ScrollTrigger } from "gsap/ScrollTrigger";

    gsap.registerPlugin(ScrollTrigger);
    let title;
   let wrapper;
    import { onMount } from "svelte";
    onMount(() => {
        gsap.to(title, {
            scrollTrigger: {
                trigger: title,
                toggleActions: "restart pause reverse none",
                start: "20px 75%",
                scrub:1,
                end: "+=300",
            },
            scaleX: 1.1,
            duration: 2,
            yoyoEase: true,
        });
    });
</script>

<div bind:this={wrapper}>
    <h3>Hi,</h3>
    <h2>TEJASWINI</h2>
    <h3>here, well I am a</h3>
    <h2 bind:this={title}>DESIGNER</h2>
</div>

<style>
    div > h2:first-of-type {
        font-size: 4rem;
        line-height: 1;
    }
    h2:last-child {
        scale: 1;
        font-size: clamp(6rem,8rem,10rem);
        line-height: 1;
        font-family: "Banigar";
        transform-origin: left;
    }
    h6 {
        font-size: 1rem;
    }
</style>
