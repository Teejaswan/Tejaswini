<script>
    import { gsap } from "gsap";

    import { ScrollTrigger } from "gsap/ScrollTrigger";

    gsap.registerPlugin(ScrollTrigger);

    let title;
    let line;
    import { onMount } from "svelte";

    onMount(() => {
        gsap.to(title, {
            scaleX: 1.1,
            duration: 0.3,
            delay: 0.5,
            skewX: "-20deg",
            transformOrigin: "left bottom",
            yoyoEase: true,
            scrollTrigger: {
                trigger: title,
                start: "center center",
                end: "+=30px",
                scrub: 1,
                toggleActions: "restart none reverse none",
            },
        });
        gsap.to(line, {
            scaleX: 10,
            transformOrigin: "left",
            yoyoEase: true,
            scrollTrigger: {
                trigger: line,
                start: "center center",
                end: "+=30px",
                scrub: 1,
                toggleActions: "restart none reverse none",
            },
        });
    });
</script>

<div class="flex-container">
    <hr bind:this={line} />
    <div class="wrapper">
        <h4><i>Versatile</i></h4>
        <h3 bind:this={title}>Skills</h3>
    </div>
</div>

<style>
    .flex-container {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
        margin-block-end: 8rem;
    }

    .wrapper {
    }
    hr {
        border: none;
        height: 0.1px;
        width: 9%;
        color: white;
        background-color: white;
    }

    h4,
    h3 {
        text-align: end;
    }

    h4 {
        font-size: 1rem;
    }

    h3 {
        font-size: 2rem;
        font-family: var(--titlefont);
    }
</style>
