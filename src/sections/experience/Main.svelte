<script>
    import Cds from "./components/CDS.svelte";
    import Others from "./components/Others.svelte";
    import Header from "./components/Header.svelte";
</script>

<section>
 <Header></Header>
 <Cds></Cds>
 <Others></Others>
</section>

<style>
    section{
       padding-block-start: 10rem;
    }
</style>