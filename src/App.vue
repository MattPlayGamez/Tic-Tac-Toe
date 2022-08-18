<template>
<h1>Tic Tac Toe</h1>
<div><button @click="msg('Play Tic Tac Toe like normal.\nBut with a little twist. Play to find out')">More info</button></div>
  <section name="app" id="grid">
    <div @click="click(0)" class="cell">
      <p>{{ cells[0] }}</p>
    </div>
    <div @click="click(1)" class="cell">
      <p>{{ cells[1] }}</p>
    </div>
    <div @click="click(2)" class="cell">
      <p>{{ cells[2] }}</p>
    </div>
    <div @click="click(3)" class="cell">
      <p>{{ cells[3] }}</p>
    </div>
    <div @click="click(4)" class="cell">
      <p>{{ cells[4] }}</p>
    </div>
    <div @click="click(5)" class="cell">
      <p>{{ cells[5] }}</p>
    </div>
    <div @click="click(6)" class="cell">
      <p>{{ cells[6] }}</p>
    </div>
    <div @click="click(7)" class="cell">
      <p>{{ cells[7] }}</p>
    </div>
    <div @click="click(8)" class="cell">
      <p>{{ cells[8] }}</p>
    </div>
  </section>
  <button @click="restart">Click here to restart</button>
</template>




  <script>
const winningGrid = [
  [0, 1, 2],
  [3, 4, 5],
  [6, 7, 8],
  [0, 3, 6],
  [1, 4, 7],
  [2, 5, 8],
  [0, 4, 8],
  [2, 4, 6],
]

let currentGrid = ['', '', '', '', '', '', '', '', '',]

export default {
  data() {
    return {
      cells: ['', '', '', '', '', '', '', '', ''],
      currentPlayer: 'X'
    }
  },
  methods: {
    click(number) {
      number = Number(number)
      let StartGrid = this.cells
      console.table({ StartGrid })
      console.log(number)
      StartGrid[number] = this.currentPlayer
      currentGrid[number] = this.currentPlayer
      this.cells = StartGrid
      setTimeout(() => {
        this.checkWinner()
      }, 50);
      this.currentPlayer = (this.currentPlayer === 'X') ? this.currentPlayer = 'O' : this.currentPlayer = 'X'
    },

    restart() {
      window.location.reload()
    },
    checkWinner() {
      for (let i = 0; i < winningGrid.length; i++) {
        const winning = winningGrid[i]
        const cellA = currentGrid[winning[0]]
        const cellB = currentGrid[winning[1]]
        const cellC = currentGrid[winning[2]]
        console.log(cellA, cellB, cellC)
        if (cellA == "" && cellB == "" && cellC == "") {
          continue;
        }
        if (cellA === cellB && cellB === cellC) {
          this.currentPlayer = (this.currentPlayer === 'X') ? this.currentPlayer = 'O' : this.currentPlayer = 'X'
          alert(`${this.currentPlayer} has won the game`);
          this.restart()
          break;

        }
      }

    },
    msg(message) {
      alert(message)
    }
  },
  created() {
    this.cells = ['', '', '', '', '', '', '', '', '']
  }

}
</script>


<style scoped>
#grid {
  display: grid;
  grid-template-columns: repeat(3, 10rem);
}

.cell {
  position: relative;
  text-align: center;
  align-items: center;
  height: 10rem;
  width: 10rem;
  background-color: lightslategray;
  border: 0.25rem solid white;
  font-size: 3rem;
}
</style>