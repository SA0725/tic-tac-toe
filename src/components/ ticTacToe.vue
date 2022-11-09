<template>
  <div>
    <h1>Current player: {{this.currentPlayer}}</h1>
    <button @click="reset" class="button-3">Reset</button>
    <div class="board">
      <button @click.once="determinePlayer();tile0()" :disabled="this.win===true||this.tie===true"  id="0" class="cell">{{this.tile_0}}</button>
      <button @click.once="determinePlayer();tile1()" :disabled="this.win===true||this.tie===true"  id="1" class="cell">{{this.tile_1}}</button>
      <button @click.once="determinePlayer();tile2()" :disabled="this.win===true||this.tie===true"  id="2" class="cell">{{this.tile_2}}</button>
      <button @click.once="determinePlayer();tile3()" :disabled="this.win===true||this.tie===true"  id="3" class="cell">{{this.tile_3}}</button>
      <button @click.once="determinePlayer();tile4()" :disabled="this.win===true||this.tie===true"  id="4" class="cell">{{this.tile_4}}</button>
      <button @click.once="determinePlayer();tile5()" :disabled="this.win===true||this.tie===true"  id="5" class="cell">{{this.tile_5}}</button>
      <button @click.once="determinePlayer();tile6()" :disabled="this.win===true||this.tie===true"  id="6" class="cell">{{this.tile_6}}</button>
      <button @click.once="determinePlayer();tile7()" :disabled="this.win===true||this.tie===true"  id="7" class="cell">{{this.tile_7}}</button>
      <button @click.once="determinePlayer();tile8()" :disabled="this.win===true||this.tie===true"  id="8" class="cell">{{this.tile_8}}</button>
    </div>
  <h1>{{this.winner}}</h1>
  <h1>{{this.msg}}</h1>
  </div>
</template>

<script>
export default {
  data(){
    return{
      playerO: "O",
      playerX: "X",
      currentPlayer:'O',
      previousPlayer:"",
      tile_0: "",
      tile_1: "",
      tile_2: "",
      tile_3: "",
      tile_4: "",
      tile_5: "",
      tile_6: "",
      tile_7: "",
      tile_8: "",
      winner: null,
      win: false,
      tie:false,
      msg: '',

    }
  },
  methods:{
    determinePlayer(){
      if(this.currentPlayer === ''){
        this.currentPlayer = this.playerO
      }
      else if(this.currentPlayer === this.playerO){
        this.currentPlayer = this.playerX
      }
      else if(this.currentPlayer === this.playerX){
        this.currentPlayer = this.playerO
      }
      this.determinePreviousPlayer()
      
  },
  determinePreviousPlayer(){
      if(this.previousPlayer === ''){
        this.previousPlayer = this.playerO
      }
      else if(this.currentPlayer === this.playerX){
        this.previousPlayer = this.playerO
      }
      else if(this.currentPlayer === this.playerO){
        this.previousPlayer = this.playerX
      }
      
  },
  findResult(){
    this.findWin()
    this.findTie()
  },
  tile0(){
    if (this.currentPlayer === "O"){
      this.tile_0 = "X"
    }else{
      this.tile_0 = "O"
    }
    this.findResult()
    },
  tile1(){
    if (this.currentPlayer === "O"){
      this.tile_1 = "X"
    }else{
      this.tile_1 = "O"
    }this.findResult()
  },
tile2(){
    if (this.currentPlayer === "O"){
      this.tile_2 = "X"
    }else{
      this.tile_2 = "O"
    }this.findResult()
  },
  tile3(){
    if (this.currentPlayer === "O"){
      this.tile_3 = "X"
    }else{
      this.tile_3 = "O"
    }this.findResult()
  },
  tile4(){
    if (this.currentPlayer === "O"){
      this.tile_4 = "X"
    }else{
      this.tile_4 = "O"
    }this.findResult()
  },
  tile5(){
    if (this.currentPlayer === "O"){
      this.tile_5 = "X"
    }else{
      this.tile_5 = "O"
    }this.findResult()
  },
  tile6(){
    if (this.currentPlayer === "O"){
      this.tile_6 = "X"
    }else{
      this.tile_6 = "O"
    }this.findResult()
  },
  tile7(){
    if (this.currentPlayer === "O"){
      this.tile_7 = "X"
    }else{
      this.tile_7 = "O"
    }this.findResult()
  },
  tile8(){
    if (this.currentPlayer === "O"){
      this.tile_8 = "X"
    }else{
      this.tile_8 = "O"
    }this.findResult()
  },
  findWin(){
    if((this.tile_0!==''&&this.tile_0===this.tile_1&&this.tile_1===this.tile_2)||
    (this.tile_0!==''&&this.tile_0===this.tile_3&&this.tile_3===this.tile_6)||
    (this.tile_3!==''&&this.tile_3===this.tile_4&&this.tile_4===this.tile_5)||
    (this.tile_6!==''&&this.tile_6===this.tile_7&&this.tile_7===this.tile_8)||
    (this.tile_1!==''&&this.tile_1===this.tile_4&&this.tile_4===this.tile_7)||
    (this.tile_5!==''&&this.tile_5===this.tile_2&&this.tile_2===this.tile_8)||
    (this.tile_0!==''&&this.tile_0===this.tile_4&&this.tile_4===this.tile_8)||
    (this.tile_2!==''&&this.tile_2===this.tile_4&&this.tile_2===this.tile_6)){
      this.winner = `The winner is ${this.previousPlayer}!`;
      this.win = true;
      return this.win
    }else{
      this.winner = null;
      return this.win
    }
  } ,
  findTie(){
    if ((this.tile_0!==''&&this.tile_1!==''&&
    this.tile_2!==''&&this.tile_3!==''&&
    this.tile_4!==''&&this.tile_5!==''&&
    this.tile_6!==''&&this.tile_7!==''&&
    this.tile_8!=='')&&this.findWin()===false){
      this.tie=true
      this.msg = "It is a Tie!"
    }
  },
  reset(){
    window.location.reload();
  }
}
}
</script>

<style scoped>

.board{
  width: 360px;
  margin: 30px auto;
  background-color: rgb(255, 255, 255);
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: minmax(120px,auto);
  font-size: 16px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
}
.cell{
  font-size: 36px;
  font-weight: bolder;
  border: 1px solid rgb(176, 176, 176);
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
}
.cell:disabled{
  color: rgb(158, 158, 158);
}
.button-3 {
  background-color: #2c3e50;
  border: 1px solid rgba(27, 31, 35, .15);
  border-radius: 6px;
  box-shadow: rgba(27, 31, 35, .1) 0 1px 0;
  box-sizing: border-box;
  color: #fff;
  cursor: pointer;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  font-size: 20px;
  font-weight: 600;
  line-height: 20px;
  padding: 9px 24px;
}

.button-3:focus:not(:focus-visible):not(.focus-visible) {
  box-shadow: none;
  outline: none;
}

.button-3:hover {
  background-color: #3a526a;
}

</style>
