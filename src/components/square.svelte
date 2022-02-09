<script lang="ts">
    import { scale } from "svelte/transition";
    export let style;
    export let onClick;
    export let value;
</script>

<button style={style} on:click={onClick} class="square">
    {#if value != null}
        <div transition:scale>{value}</div>
    {/if}
</button>

<style>

</style>