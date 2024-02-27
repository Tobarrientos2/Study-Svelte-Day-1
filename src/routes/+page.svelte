<script>
    import Board from "$lib/Board.svelte";
    import { mWin } from "$lib/utils";

let g_arr_txt = Array(9).fill('');
let txt_i = 'x';

$: g_arr_arr = mWin(g_arr_txt);
</script>

<div class="container">
    <Board size={3}>
    <svelte:fragment slot="game">
        {#each g_arr_txt as txt_o, i}
            <button 
            class="square"
            class:winning={g_arr_arr?.includes(i)}
            disabled={txt_o}
            on:click={() => {
                g_arr_txt[i] = txt_i;
                txt_i = txt_i === 'x' ? 'o': 'x';
            }}
>
{txt_o}
            </button>
        {/each}
    </svelte:fragment>
    </Board>
 
</div>


<style>
    .square, .square:disabled{
        background: white;
        color: black;
        font-size: 2em;
        opacity: 1;
    } 
    .container {
        display: flex;
        flex-direction: column;
        gap: 1em;
        align-items: center;
        justify-content: center;
        height:100vh;
        margin: 0 auto;
    
    }

    .winning{
        font-weight: bold;
    } 
    .container:has(.winning) .square:not(.winning){
        color: #ccc;
    } 
</style>