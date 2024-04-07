<!-- <script>


    let imageVisible = false;
    let imageX = 0;
    let imageY = 0;
    let fadeOut = false;
    let moveUp = false;
    let currentImage = "";

    function handleClick(event) {
        const rect = event.target.getBoundingClientRect();
        imageX = event.clientX - rect.left;
        imageY = event.clientY - rect.top;
        imageVisible = false;

        const randomIndex = Math.floor(Math.random() * images.length);
        currentImage = images[randomIndex];
        fadeOut = false;
        moveUp = false;
        setTimeout(() => {
            imageVisible = true;
            moveUp = true;
            fadeOut = true;
        }, 500);
    }

    $: leftStyle = `left: ${imageX}px;`;
    $: topStyle = `top: ${imageY}px;`;
    $: opacityStyle = `opacity: ${imageVisible ? 1 : 0};`;
    $: transitionStyle = `transition: ${moveUp ? "transform 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275), opacity 1s ease-out" : "none"};`;
    $: transformStyle = `transform: ${moveUp ? "translateY(-60px)" : "none"};`;

    function clearImage() {
        imageVisible = false;
    }
</script>

<div on:mousemove={handleClick} role="none" class="wrapper">
    <div
        class="image"
        style={leftStyle +
            topStyle +
            opacityStyle +
            transitionStyle +
            transformStyle}
        on:transitionend={clearImage}
    >
        <div class="texture"></div>
        <img src={currentImage} alt="design-works" />
    </div>
</div>

<style>
    .wrapper {
        position: absolute;
        z-index: 10;
        width: 85%;
        height: 75%;
        left: 0;
        right: 0;
        top: 0;
        bottom: 0;
        margin: auto;
    }
    img {
        width: 100%;
        height: 100%;
    }
    .texture {
        position: absolute;
        background: radial-gradient(circle at center, rgba(255, 0, 0,0.5) 0%, black 100%);
        z-index: 100;
        width: 100%;
        height: 100%;
    }
    .image {
        display: block;
        position: absolute;
        width: 15rem;
        height: 15rem;
-webkit-mask-image: radial-gradient(circle, rgba(0,0,0,1) 0%, rgba(255,0,0,0.4) 50%);
mask-image: radial-gradient(circle, rgba(0,0,0,1) 0%, rgba(0,0,0,0) 70%);

    }
</style> -->
