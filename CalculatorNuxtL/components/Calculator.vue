 <template>

<div class="calculator">
    <div class="display">{{showDisplay}}</div>
    <div class="cal_body">
        <button  @click="append('7')" class="btnc s_button">7</button>
        <button  @click="append('8')" class="btnc s_button">8</button>
        <button  @click="append('9')" class="btnc s_button">9</button>
        <button  @click="plus" class="btnc s_button">+</button>
        <button  @click="append('4')" class="btnc s_button">4</button>
        <button  @click="append('5')" class="btnc s_button">5</button>
        <button  @click="append('6')" class="btnc s_button">6</button>
        <button  @click="minus" class="btnc s_button">-</button>
        <button  @click="append('1')" class="btnc s_button">1</button>
        <button  @click="append('2')" class="btnc s_button">2</button>
        <button  @click="append('3')" class="btnc s_button">3</button>
        <button  @click="multiply" class="btnc s_button">x</button>
        <button  @click="del" class="btnc delete s_button">ลบ</button>
        <button  @click="append('0')" class="btnc s_button">0</button>
        <button  @click="dot" class="btnc s_button">.</button>
        <button  @click="divide" class="btnc s_button">÷</button>
        <button  @click="clear" class="btnc clear">เคลียร์</button>
        <button  @click="equal" class="btnc s_button">=</button>
    </div>
    
</div>
</template>

<script>
export default {
data(){
return{
showDisplay: '',
previous: null,
operator: null,
operatorClicked: false,
    }
},
methods:{
    clear(){
    his.showDisplay = '' ;
    },
    append(nummber){
    if (this.operatorClicked){
        this.showDisplay = '';
        this.operatorClicked = false;
    }
    this.showDisplay = `${this.showDisplay}${nummber}`
    },
    dot(){
    if(this.showDisplay.indexOf('.') === -1){
        this.append('.');
    }
    },

    setPrenum(){
    this.previous = this.showDisplay;
    this.operatorClicked = true;
    },
    plus(){
    this.operator = (a,b) => a + b;
    this.setPrenum();
    },
    minus(){
    this.operator = (a,b) => b - a;
    this.setPrenum();
    },
    multiply(){
      this.operator = (a,b) => a * b;
    this.setPrenum();
    },
    divide(){
    this.operator = (a, b) => b / a;
    this.setPrenum();
    },
    equal(){
    this.showDisplay = `${this.operator(parseFloat(this.showDisplay), parseFloat(this.previous))}`;
    this.previous = null;
    },
    del(){
this.showDisplay = this.showDisplay.substring(0,this.showDisplay.length-1);
},
}
}
</script>


