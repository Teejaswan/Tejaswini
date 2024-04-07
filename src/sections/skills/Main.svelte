<script>
    import Draggable from "./components/Draggable.svelte";
    import Header from "./components/Header.svelte";
    const skills = [
        // Design
        "Graphic Design",
        "User Interface",
        "User Experience",
        "Prototyping",
        "Digital Illustration",
        "Character Design",
        "3D Modelling",
        "Motion Graphics",
        "Animation",
        "Color Theory",

        // Graphic Design
        "Poster Design",
        "Branding",
        "Logo Design",
        "Typography",
        "Iconography",
        "Color",
        "Guidelines",

        // Software
        "Adobe Illustrator",
        "Adobe Photoshop",
        "Adobe After Effects",
        "Blender",
        "Figma",

        // Front-End Development
        "HTML",
        "CSS",
        "JavaScript",
        "TypeScript",
        "Svelte",
        "React",
        "Vite",
        "Tailwind CSS",
        "Semantic HTML",
        "PostCSS",
        "Design System",
        "Git",
        "Li",
    ];

    let skillChips = [];
    function chipsrandom() {
        skills.forEach((skill) => {
            const chip = {
                text: skill,
                left: `${Math.random() * 80}vw`,
                top: `${Math.random() * 80}vh`,
            };
            skillChips = [...skillChips, chip];
        });
    }

    chipsrandom();
</script>

<Header></Header>
<section>
    <h3>Grab me!</h3>
    {#each skillChips as chip, i}
        <Draggable>
            <div
                class="chip"
                style="left: {chip.left}; top: {chip.top}; font-size: max(1.5vw,2vh); transform: scale({1 -
                    i / 100});"
            >
                {chip.text}
            </div>
        </Draggable>
    {/each}
</section>

<style>
    h3 {
        display: flex;
        align-items: center;
        justify-content: center;
        height: 100%;
        font-size: 10vw;
        font-family: var(--titlefont);
        opacity: 0.25;
    }
    section {
        width: 100%;
        height: 100vh;
        position: relative;
    }
    .chip {
        position: absolute;
        padding: 5px 10px;
        white-space: nowrap;
        color: #fff;
        background-color: rgba(255, 0, 0, 0.5);
        backdrop-filter: blur(50px);
        border-radius: 20px;
        cursor: grab;
        transition: transform 0.3s ease;
    }
</style>
