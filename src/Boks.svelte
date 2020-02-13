<script>
    import {db} from "./firebase.js"
    const dbBokser = db.collection("dbBokser")

    export let id = ""
    export let data = {}

    const changeCSS = () => {
        const boks = dbBokser.doc(id)
        boks.update({
            css: data.css
        })
    }

</script>

<textarea style={data.css} bind:value={data.css} on:input={changeCSS}></textarea>


<style>

    textarea {
        transition: 2s;
    }


    textarea:focus {
        outline: none;
    }

</style>