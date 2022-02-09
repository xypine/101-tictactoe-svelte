<script lang="ts">
    import { calculateWinner } from "../utils/utils";
    import HistoryManager from "./historyManager.svelte";
    import Board from "./board.svelte";
    let history = [
        {
            squares: [
                null, null, null,
                null, null, null,
                null, null, null,
            ],
            xIsNext: true,
        },
    ];
    let current;
    let winner;
    $: current = history[history.length - 1];
    $: if(current){
        winner = calculateWinner(current.squares);
    }
    let status;
    $: if (winner) {
      status = 'Winner: ' + winner;
    }
    else if(current.xIsNext != null) {
      status = 'Next player: ' + (isXnext() ? 'X' : 'O');
    }


    function rollbackHistory(index) {
        history = history.slice(0, index);
    }
    function isXnext() {
        return current.xIsNext;
    }
    function handleClick(i) {
        let squares = current.squares.slice();
        if (calculateWinner(squares) || squares[i]) {
            return;
        }
        if(squares[i] == null){
            squares[i] = isXnext() ? 'X' : 'O';
        }
        const newHistory = [
            ...history, 
            {
                squares: squares,
                xIsNext: !isXnext()
            } 
        ];
        history = newHistory;
    }
</script>

<main>
    <div class="game">
        <div class="game-history">
            <HistoryManager history={history} rollbackHistoryCallback={ rollbackHistory } winner={winner} />
        </div>
        <div class="game-board">
            <Board squares={current.squares} handleClick={ handleClick } winner={winner} />
        </div>
        <div class="game-info">
            <div>{status}</div>
            <ol><!--TODO */}--></ol>
        </div>
    </div>
</main>''

<style>
    
</style>