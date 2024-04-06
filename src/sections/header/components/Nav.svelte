<script>
    function scrollIntoView({ target }) {
        const el = document.querySelector(target.getAttribute("href"));
        if (!el) return;
        el.scrollIntoView({
            behavior: "smooth",
        });
    }
</script>

<nav>
    <ul>
        <li class="red">
            <a href="#footer" on:click|preventDefault={scrollIntoView}
                >Contact</a
            >
        </li>
        <li class="red">
            <a
                href="https://drive.google.com/file/d/1O0vuIacm16RK6N9LIDPAixomgX9vEsE8/view?usp=drive_link"
                target="_blank">Resume</a
            >
        </li>
    </ul>
</nav>

<style>
    nav {
        position: fixed;
        top: 0;
        right: 0;
        width: 100%;
        backdrop-filter: blur(10px);
        z-index: 1000;
    }
    ul {
        width: 100%;
        display: flex;
        justify-content: flex-end;
        padding: 1.5rem 3rem 1rem 1.5rem;
        gap: 3rem;
        background: rgb(255, 255, 255);
        background: linear-gradient(
            0deg,
            rgba(255, 0, 0, 0) 0%,
            rgba(255, 0, 0, 0.25) 100%
        );
    }
    a {
        text-decoration: underline;
        cursor: pointer;
        color: white;
    }
</style>
