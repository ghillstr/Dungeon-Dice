<template>
<form>
    
    <tr id="dice">
        <td id="dice-type">d6</td>
        <td class="img"><img id="SixSidedDieImg" src="@/assets/ClipartKey_215814.png" alt="6 Sided Die" v-on:click="diceRoll" ></td>
        <td><input id="numberOfDice" type="number" value="1" min="1" v-model.number="diceNumber"></td>
        <td><input type="number" id="d6mo" value="0" v-model.number="d6mo"></td> 
        <td><button id= "d6btn" type="button" v-on:click= "diceRoll">Roll</button></td>
        <td id="result">{{modifiedDice}}</td>
        <td id="details">{{details}}{{d6mo}}</td>
        </tr>
       
</form> 
</template>
<script>
import axios from 'axios';

export default {
    name: 'd6Value',
    data(){
        return {
            result : '0',
            diceNumber : '1',
            details: '',
            d6mo : '0',
            dNum : '1'

         }

    },
    computed:{
        modifiedDice() {
            let modDice = parseInt(this.result) + parseInt(this.d6mo) ;
             return modDice 
        }

    },
    

    methods:{
        diceRoll() {
            axios.get('https://rolz.org/api/?' + this.diceNumber + 'd20.json')
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

#SixSidedDieImg {
    width : 50px;
}
#d6mo {
    width : 30%;
}

</style>