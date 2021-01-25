<template>
<form>
    
    <tr id="dice">
        <td id="dice-type">d8</td>
        <td class="img"><img id="EightSidedDieImg" src="@/assets/8-sided-die.png" alt="8 Sided Die" v-on:click="diceRoll" ></td>
        <td><input id="numberOfDice" type="number" value="1" min="1" v-model.number="diceNumber"></td>
        <td><input type="number" id="d8mo" value="0" v-model.number="d8mo"></td> 
        <td><button id= "d8btn" type="button" v-on:click= "diceRoll">Roll</button></td>
        <td id="result">{{modifiedDice}}</td>
        <td id="details">{{details}}{{d8mo}}</td>
        </tr>
       
</form> 
</template>
<script>
import axios from 'axios';

export default {
    name: 'd8Value',
    data(){
         return {
            result : '0',
            diceNumber : '1',
            details: '',
            d8mo : '0',
            dNum : '1'

         }
    },
    computed:{
        modifiedDice() {
            let modDice = parseInt(this.result) + parseInt(this.d8mo) ;
             return modDice 
        }

    },
    

    methods:{
      diceRoll() {
            axios.get('https://rolz.org/api/?' + this.diceNumber + 'd8.json')
            .then( (response) => {
                this.result = response.data.result;
                this.details = response.data.details;
             })
             .catch(err => {
                 console.log(err);
                 
             })
           
        }
    }



}
</script>

<style>

#EightSidedDieImg {
    width : 50px;
}
#d8mo {
    width : 30%;
}


</style>