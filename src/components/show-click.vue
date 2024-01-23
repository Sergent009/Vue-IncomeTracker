<template>
    <div>
        <h2>Congratulations! You SuccessFully Logged In.</h2>
        
        <div class="calculator">
           <input type="text" class="inputPoint" v-model="count" >
            <div>
                <button @click="()=>{updDisplay('+')}" class="operator">+</button>
                <button @click="()=>{updDisplay('-')}" class="operator">-</button>
                <button @click="()=>{updDisplay('*')}" class="operator">*</button>
                <button @click="()=>{updDisplay('/')}" class="operator">/</button>
            </div>
              <div>
                <button @click="()=>{updDisplay('1')}" class="numbers">1</button>
                <button @click="()=>{updDisplay('2')}" class="numbers">2</button>
                <button @click="()=>{updDisplay('3')}" class="numbers">3</button>
            </div>
              <div>
                <button @click="()=>{updDisplay('4')}" class="numbers">4</button>
                <button @click="()=>{updDisplay('5')}" class="numbers">5</button>
                <button @click="()=>{updDisplay('6')}" class="numbers">6</button>
            </div>
              <div>
                <button @click="()=>{updDisplay('7')}" class="numbers">7</button>
                <button @click="()=>{updDisplay('8')}" class="numbers">8</button>
                <button @click="()=>{updDisplay('9')}" class="numbers">9</button>
            </div>
            <div>
                <button @click="clearDisplay" class="res">C</button>
                <button @click="calResult" class="res">=</button>
            </div>

            </div>        
    </div>
</template>

<script>
    export default {
        name: 'showClick',

        data(){
            return{
                count: '',
                result: ''
            }
        },

        methods: {
            updDisplay(val){
                this.count = this.count + val
            },
            clearDisplay(){
                this.count = ''
            },
            calResult(){
                this.result = eval(this.count)
                this.count = this.result
            }
        }
    }
</script>

<style scoped>
h2{
    position: absolute;
    top:5px;
    left: 350px;
    border: 3px solid black;
    border-radius: 10px;
    padding: 10px 30px;
    color: rgb(22, 21, 21);
    background: linear-gradient(100deg, rgb(96, 141, 158), rgb(74, 74, 143));
}

.calculator{
    width: 34vw;
    height: 38vw;
    background: burlywood;
    position: absolute;
    top: 110px;
    left: 420px;
    border: 2px solid black;
    border-radius: 10px;
}

.inputPoint{
    width: 32vw;
    height: 4vw;
    background: white;
    position: absolute;
    top: 25px;
    left: 13px;
    border: 2px solid black;
    border-radius: 10px;
    font-size: 30px;
}

.operator{
  padding: 13px 31px;
  margin: 15px;
  margin-top: 120px;
  border: 2px solid black;
  border-radius: 10px;
  font-size: 18px;
  background: black;
  color: white;
  cursor: pointer;
}

.numbers{
    padding: 12px 35px;
    margin: 12px;
    font-size: 18px;
    background: grey;
    color: white;
    border: 1px solid black;
    border-radius: 10px;
    cursor: pointer;
}

.res{
    padding: 9px 60px;
    margin: 15px;
    font-size: 18px;
    border: 2px solid black;
    border-radius: 10px;
    background: black;
    color: white;
    cursor: pointer;
}

</style>