<script>
    export let left = 0;
    export let top = 0;

    let moving = false;

    function onMouseDown() {
        moving = true;
    }

    function onMouseMove(e) {
        if (moving){

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
