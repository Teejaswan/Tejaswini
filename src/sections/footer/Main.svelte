<script>
    import linkedin from "./assets/linkedin.svg";
    import behance from "./assets/behance.svg";
    import email from "./assets/email.png";

    import { gsap } from "gsap";

    import { ScrollTrigger } from "gsap/ScrollTrigger";

    gsap.registerPlugin(ScrollTrigger);
    let title;
    import { onMount } from "svelte";
    onMount(() => {
        gsap.to(title, {
            scrollTrigger: {
                trigger: title,
                toggleActions: "restart pause reverse none",
                start: "20px 75%",
                scrub: 1,
                end: "+=300",
            },
            scaleX: 1.1,
            duration: 2,
            yoyoEase: true,
        });
    });
</script>

<section id="footer">
    <a href="mailto:teejaswan12@gmail.com" class="red git"> Get in touch </a>
    <div>
        <nav>
            <ul>
                <li>
                    <a
                        href="https://www.behance.net/tejaswini_design"
                        target="_blank"
                        ><img src={behance} alt=" " class="red" /></a
                    >
                </li>
                <li>
                    <a
                        href="https://www.linkedin.com/in/tejaswini-design/"
                        target="_blank"
                        ><img src={linkedin} alt=" " class="red" /></a
                    >
                </li>
                <li>
                    <a href="mailto:teejaswan12@gmail.com"
                        ><img src={email} alt=" " class="red" /></a
                    >
                </li>
            </ul>
        </nav>
        <h2 bind:this={title}>Tejaswini</h2>
    </div>
</section>

<style>
    section {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-items: flex-end;
        margin-block-start: 4rem;
    }
    div {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: baseline;
        transform: translate(15px, 40px);
        width: 100%;
    }
    ul {
        display: flex;
        flex-direction: row;
        gap: 1rem;
    }
    img {
        color: white;
        display: block;
        max-width: 1.5rem;
        aspect-ratio: 1;
    }
    .red {
        font-size: 2rem;
        color: white;
        background-color: transparent;
        border: none;
        cursor: pointer;
    }

    h2 {
        font-size: 10vw;
        font-family: var(--titlefont);
        transform-origin: right;
    }
    @media screen and (max-width: 700px) {
        h2 {
            font-size: clamp(2rem, 3rem, 5rem);
        }
        .git {
            font-size: 1.5rem;
        }
    }
    @media screen and (max-width: 500px) {
        div {
            flex-direction: column;
        }
    }
</style>
