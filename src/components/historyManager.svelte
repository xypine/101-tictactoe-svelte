<script lang="ts">
    import { scale } from "svelte/transition";
    import { flip } from "svelte/animate"
    import { getStatusColor } from "../utils/utils";
    export let rollbackHistoryCallback;
    export let previewIndex;
    export let history;
    export let winner;
</script>

<main>
    <div class="history-container">
        {#each history.slice(1) as i,index (i)}
            <button 
                class="history-element history-button" 
                on:click={ () => rollbackHistoryCallback( (index) + 1 ) } 
                on:mouseover={ (e) => {previewIndex = index; e.stopPropagation()}} 
                on:mouseleave={ ()=>{previewIndex=null}} 
                on:focus={null}
                in:scale
                out:scale={{delay: 50*index}}
                animate:flip
            >
                { index == 0 ? "Start" : (index) + 1}
            </button> 
        {/each}
        <button class="history-element" style="--bg: {getStatusColor(winner)};">
            Current
        </button>
    </div>
</main>

<style>
    
</style>