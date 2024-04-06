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
                left: `${Math.random() * 90}vw`,
                top: `${Math.random() * 90}vh`,
            };
            skillChips = [...skillChips, chip];
        });
    }

    chipsrandom();
</script>

<Header></Header>
<section>
    {#each skillChips as chip, i}
        <Draggable>
            <div
                class="chip"
                style="left: {chip.left}; top: {chip.top}; font-size:{22 -
                    i / 4}px"
            >
                {chip.text}
            </div>
        </Draggable>
    {/each}
</section>

<style>
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
        cursor: pointer;
        transition: transform 0.3s ease;
    }
</style>
