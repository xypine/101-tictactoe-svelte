<script lang="ts">
    export let style;
    export let onClick;
    export let value;
</script>

<button style={style} on:click={onClick} class="square">
    {#if value != null}
        {value}
    {/if}
</button>

<style>

</style>