<script lang="ts">
    import { getStatusColor } from "../utils/utils";
    export let rollbackHistoryCallback;
    export let history;
    export let winner;
</script>

<main>
    <div class="history-container">
        {#each history as i,index}
            <button class="history-element history-button" on:click={ () => rollbackHistoryCallback( (index) + 1 ) }>
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