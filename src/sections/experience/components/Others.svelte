<script>
    import { onMount } from "svelte";
    import { gsap } from "gsap";

    import { ScrollTrigger } from "gsap/ScrollTrigger";

    gsap.registerPlugin(ScrollTrigger);
    let first, second, container, third;
    let sections = [];
    let zoom = [];
    onMount(() => {
        const sectionDivs = container.querySelectorAll(".section");
        sections = Array.from(sectionDivs);
        gsap.to(sections, {
            xPercent: -100 * (sections.length - 1),
            ease: "none",
            scrollTrigger: {
                trigger: container,
                pin: true,
                scrub: 1,
                // snap: 1 / (sections.length - 1),
                end: () => "+=" + container.offsetWidth,
            },
        });
        gsap.to(first, {
            translateX: 5,
            duration: 3,
            yoyoEase: true,
            scrollTrigger: {
                trigger: first,
                start: "top center",
                end: "top top",
                toggleActions: "restart pause reverse resume",
                scrub: 1,
            },
        });

        gsap.to(second, {
            translateX: 50,
            duration: 2,
            yoyoEase: true,
            scrollTrigger: {
                trigger: second,
                start: "top center",
                end: "top top",
                toggleActions: "restart pause reverse resume",
                scrub: 1,
            },
        });
        gsap.to(third, {
            translateX: -50,
            duration: 2,
            yoyoEase: true,
            scrollTrigger: {
                trigger: third,
                start: () => 3 * sections[3].offsetWidth + "center",
                end: "+=100%",
                toggleActions: "restart pause reverse resume",
                scrub: 1,
            },
        });
        const illuImgs = container.querySelectorAll(".illu-img");
        illuImgs.forEach((illuImg, i) => {
            gsap.to(illuImg, {
                marginBottom: Math.random() * 100,
                marginLeft: Math.random() * 100,
                duration: 1,
                yoyoEase: true,
                scrollTrigger: {
                    trigger: sections[2],
                    start: () => 2 * sections[2].offsetWidth + 100 + "center",
                    end: "+=100%",
                    toggleActions: "restart pause reverse resume",
                    scrub: 1,
                },
            });
        });
        const zoomDivs = container.querySelectorAll(".zoom");
        zoom = Array.from(zoomDivs);
        gsap.to(zoom, {
            scale: 1.1,
            duration: 1,
            yoyoEase: true,
            scrollTrigger: {
                trigger: sections[1],
                start: () => sections[1].offsetWidth + "top",
                end: "+=50%",
                toggleActions: "restart pause reverse resume",
                scrub: 1,
            },
        });
    });
    import img1 from "../assests/im1.jpg";
    import martin_brand from "../assests/martin_brand.png";
    import sd_brand from "../assests/sd_brand.png";
    import gundus_cd from "../assests/gundus_cd.png";
    import ill1 from "../assests/ill1.png";
    import ill2 from "../assests/ill2.png";
    import ill3 from "../assests/ill3.png";
    import ill4 from "../assests/ill4.png";
    import tby_1 from "../assests/tby_1.jpeg";
    import tby_2 from "../assests/tby_2.jpeg";
    import tby_3 from "../assests/tby_3.jpeg";
    let projectlist = [
        {
            name: "Branding",
            projects: [
                { name: "Zest", img: martin_brand },
                { name: "Sweet dreams", img: sd_brand },
            ],
        },
        {
            name: "Character Design",
            projects: [{ name: "Gundus", img: gundus_cd }],
        },
        {
            name: "motion design",
            projects: [
                {
                    name: "To be you",
                    img: tby_1,
                },
                {
                    name: "To be you",
                    img: tby_2,
                },
                {
                    name: "To be you",
                    img: tby_3,
                },
            ],
        },

        {
            name: "Illustrations",
            projects: [
                { name: "The Creation", img: ill1 },
                { name: "The Creation", img: ill2 },
                { name: "The Creation", img: ill3 },
                { name: "The Creation", img: ill4 },
            ],
        },
    ];
</script>

<div class="wrapper" bind:this={container}>
    <div class="section branding">
        <div class="images">
            {#each projectlist[0]["projects"] as projects, i}
                {console.log(projectlist[0]["projects"].length - 1 == i)}
                <a
                    href={i == 0
                        ? "https://www.behance.net/gallery/183311335/Brand-Identity-Martin-Zest "
                        : "https://www.behance.net/gallery/182852861/Logo-design-Sweet-Dreams-bakery "}
                    target="_blank"
                >
                    <div
                        class="img-wrap"
                        bind:this={first}
                        style={projectlist[0]["projects"].length - 1 == i
                            ? "width:20vw;aspect-ratio:3/4;transform:translate(150px,-100px)"
                            : "width:35vw"}
                    >
                        <img
                            src={projects.img}
                            alt={projects.name}
                            style="width: 100%;height:100%;"
                        />
                    </div>
                </a>
            {/each}
        </div>
        <div class="content">
            <h2 style="position:relative;z-index: 100;">Branding</h2>
            <p bind:this={second}>
                ❛ Crafting empathetic brand experiences that resonate with users
                and foster lasting connections.
            </p>
        </div>
    </div>
    <div class="section character">
        {#each projectlist[1]["projects"] as { name, img }}
            <a
                href="https://www.behance.net/gallery/186433109/Character-Design-Gundus"
                target="_blank"
                class="img-wrap"
            >
                <img src={img} alt={name} class="zoom" />
            </a>
            <div class="content">
                <h2 class="zoom">Character Design</h2>
                <p>
                    ❛ Infusing traits with personality, breathing life into
                    characters that captivate and engage audiences.
                </p>
            </div>
        {/each}
    </div>
    <div class="section illustrations">
        <div class="images">
            {#each projectlist[3]["projects"] as projects, i}
                <a
                    href={i == 0
                        ? "https://www.behance.net/gallery/183342949/Illustration-collection-A-Day-in-the-garden"
                        : "https://www.behance.net/gallery/183601625/Abstract-art-collection-The-Creation"}
                    target="_blank"
                >
                    <img
                        src={projects.img}
                        alt={projects.name}
                        style={i == 1 || i == 3
                            ? "transform:translateY(200px);"
                            : ""}
                        class="illu-img"
                    />
                </a>
            {/each}
        </div>
        <div class="content">
            <h2>Illustrations</h2>
            <p>
                ❛ Capturing emotions through art, evoking empathy and sparking
                imagination with every stroke.
            </p>
        </div>
    </div>
    <div class="section motion">
        <div class="images">
            {#each projectlist[2]["projects"] as projects, i}
                <a
                    href="https://www.behance.net/gallery/190083609/To-be-you-Animation"
                    target="_blank"
                >
                    <img
                        src={projects.img}
                        alt={projects.name}
                        style="width: 20vw;aspect-ratio:1;"
                    />
                </a>
            {/each}
        </div>
        <div class="content">
            <h2 bind:this={third}>Motion Design</h2>
            <p>
                ❛ Weaving narratives through motion, telling compelling stories
                that leave a lasting impression.
            </p>
        </div>
    </div>
</div>

<style>
    .wrapper {
        display: flex;
        width: 400%;
        flex-wrap: nowrap;
        height: 100vh;
    }
    .section {
        width: 100vw;
        height: 100vh;
    }
    .branding,
    .character,
    .illustrations {
        display: block;
        /* margin-block: 4rem; */
    }
    .content {
        pointer-events: none;
    }
    .branding {
        display: grid;
        grid-template-columns: 1fr 1fr;
        align-items: center;
        justify-items: center;
    }
    h2 {
        font-size: 5rem;
        font-family: var(--titlefont);
    }
    @media screen and (max-width: 700px) {
        h2 {
            font-size: clamp(2rem, 3rem, 5rem);
        }
    }
    p {
        font-size: 1.25rem;
    }
    @media screen and (max-width: 700px) {
        p {
            font-size: clamp(0.5rem, 0.75rem, 1rem);
        }
    }

    img {
        width: 35vw;
        aspect-ratio: 16/9;
        object-fit: cover;
    }
    .character,
    .illustrations {
        position: relative;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
    }
    .character .content,
    .illustrations .content {
        position: absolute;
        text-align: center;
    }
    .illustrations .images {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
    }
    .motion .images {
        display: grid;
        gap: 2rem;
        grid-template-areas:
            "img1 img2"
            "img1 img3";
        margin-top: 10rem;
        justify-content: space-evenly;
    }
    .motion .images a:nth-child(1) {
        grid-area: img1;
    }
    .motion .images a:nth-child(2) {
        grid-area: img2;
    }
    .motion .images a:nth-child(3) {
        grid-area: img3;
    }
    .motion {
        position: relative;
    }
    .img-wrap {
        overflow: hidden;
    }
    .motion .content {
        position: absolute;
        display: block;
        bottom: 40px;
        left: 75px;
    }
</style>