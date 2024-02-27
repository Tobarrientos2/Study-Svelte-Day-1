<script lang="ts">
export let size: number;
</script>

<div class="board" style="--size: {size}">
    <slot name="game">
    
    </slot>

</div>

<slot name="controls"></slot>

<style>
    .board{
        display: grid;
        height: 100%;   
        max-height: 20em;
        grid-template-columns: repeat(var(--size), 1fr);
        grid-template-rows: repeat(var(--size) 1fr);
        background-color: black;
        aspect-ratio: 1;
        gap: 1px;
        padding:0.5em;
        border-radius: 0.2em
    }

</style>