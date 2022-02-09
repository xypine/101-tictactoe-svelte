<script lang="ts">
    import Square from "./square.svelte";
    import { getStatusColor } from "../utils/utils";
    export let squares;
    export let winner;
    export let handleClick;
</script>

<main>
    <div>
        {#each [0, 1, 2] as y}
            <div class="board-row">
                {#each [0, 1, 2] as x}
                    <!-- y*3+x is the index of the tile -->
                    <Square 
                        style={ "--bg:" + getStatusColor(winner) + ";" }
                        value={squares[y*3+x]} 
                        onClick={() => handleClick(y*3+x)} 
                    />
                {/each}
            </div>
        {/each}
    </div>
</main>

<style>
    
</style>