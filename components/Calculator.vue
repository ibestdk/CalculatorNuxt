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
    
    clear(){    // ฟังก์ชั่นเคลียร์
    this.showDisplay = '' ;
    },
    append(nummber){ //ฟังก์ชั่นเพิ่มตัวเลข
    if (this.operatorClicked){
        this.showDisplay = '';
        this.operatorClicked = false;
    }
    this.showDisplay = `${this.showDisplay}${nummber}`
    },
    dot(){  //ฟังก์ชั่นเกี่ยวกับการใส่ทศนิยม
    if(this.showDisplay.indexOf('.') === -1){
        this.append('.');
    }
    },

    setPrenum(){  //เซตค่าก่อนหน้า เเละ เปลี่ยนสถานะของเครื่องหมาย
    this.previous = this.showDisplay;
    this.operatorClicked = true;
    },
    plus(){ //ฟังก์ชั่นบวก
    this.operator = (a,b) => a + b;
    this.setPrenum();
    },
    minus(){ //ฟังก์ชั่นลบ
    this.operator = (a,b) => b - a;
    this.setPrenum();
    },
    multiply(){ //ฟังชั่นคูณ
      this.operator = (a,b) => a * b;
    this.setPrenum();
    },
    divide(){       //ฟังก์ชั่นหาร
    this.operator = (a, b) => b / a;
    this.setPrenum();
    },
    equal(){      //ฟังก์ชั่นรวมเลข
    this.current = `${this.operator(
        parseFloat(this.current), 
        parseFloat(this.previous)
    )}`;
    this.previous = null;
    },
    del(){      //ฟังก์ชั่น backspace
this.showDisplay = this.showDisplay.substring(0,this.showDisplay.length-1);
},
}
}
</script>


