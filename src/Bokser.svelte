<script>
    import Boks from "./Boks.svelte"
    import {db} from "./firebase.js"
    const dbBokser = db.collection("dbBokser")


    let bokser = []

    const addBoks = () => {
        dbBokser.add({
            css: "background-color: orange;"
        })    
    }

    dbBokser.onSnapshot(snap => {
        bokser = snap.docs
    })

</script>

<header>
    <div class="add" on:click={addBoks}>Legg til boks</div>
</header>
<section>
    {#each bokser as boks}
        <Boks id={boks.id} data={boks.data()} />
    {:else}
        <div>Klikk for å lage en boks</div>
    {/each}
</section>

<style>
    section {
        margin-top: 2rem;        
        display: grid;
        gap: 2rem;
        grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
        grid-auto-rows: 230px;
    }
    .add {
        background-color: blueviolet;
        color: white;
        padding: 1rem;
        border-radius: 1rem;
        display: inline-block;
        font-size: 1.5rem;
        cursor: pointer;
    }
</style>