<script>
    export let left = 0;
    export let top = 0;

    let moving = false;

    function onMouseDown() {
        moving = true;
    }

    function onMouseMove(e) {
        if (moving) {
            // Get the boundaries of the Main component
            // const mainWidth = window.innerWidth;
            // const mainHeight = window.innerHeight;

            // // Calculate the new position
            // const newLeft = left + e.movementX;
            // const newTop = top + e.movementY;

            // // Check if the new position is within the boundaries
            // if (
            //     newLeft >= 0 &&
            //     newTop >= 0 &&
            //     newLeft <= mainWidth &&
            //     newTop <= mainHeight
            // ) {
            //     left = newLeft;
            //     top = newTop;
            // }

            left += e.movementX;
            top += e.movementY;
            console.log(e.offsetX, e.offsetY);
        }
    }

    function onMouseUp() {
        moving = false;
    }
</script>

<section
    on:mousedown={onMouseDown}
    style="left: {left}px; top: {top}px;"
    class="draggable"
>
    <slot />
</section>

<svelte:window on:mouseup={onMouseUp} on:mousemove={onMouseMove} />

<style>
    .draggable {
        user-select: none;
        max-width: fit-content;
        max-height: 2ch;
        cursor: move;
        position: absolute;
    }
</style>
