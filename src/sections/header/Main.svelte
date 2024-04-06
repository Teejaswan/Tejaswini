<script>
    import Images from "./components/Images.svelte";
import Nav from "./components/Nav.svelte";
    import Title from "./components/Title.svelte";
    
</script>


<section>
    <Nav></Nav>
    <Title></Title>
</section>

<style>
    section{
        position: relative;
        height: 100vh;
        padding-block: 0;
        display: flex;
        flex-direction: column;
        justify-content: flex-end;
    }
</style>