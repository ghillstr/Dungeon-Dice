<template>
<form>
    
    <tr id="dice">
        <td id="dice-type">d12</td>
        <td class="img"><img id="TwelveSidedDieImg" src="@/assets/12-sided-die.png" alt="12 Sided Die" v-on:click="diceRoll" ></td>
         <td><input id="numberOfDice" type="number" value="1" min="1" v-model.number="diceNumber"></td> 
        <td><input type="number" id="d12mo" value="0" v-model.number="d12mo"></td> 
        <td><button id= "d12btn" type="button" v-on:click= "diceRoll">Roll</button></td>
        <td id="result">{{modifiedDice}}</td>
        <td id="details">{{details}}{{d12mo}}</td>
        </tr>
       
</form> 
</template>
<script>
import axios from 'axios';

export default {
    name: 'd12Value',
    data(){
        return {
            result :  '0',
            diceNumber : '1',
            details : '',
            d12mo : '0',
            dNum : '1',
         }

    },
    computed:{
        modifiedDice() {
            let modDice = parseInt(this.result) + parseInt(this.d12mo) ;
             return modDice 
        }

    },
    

    methods:{
       diceRoll() {
            axios.get('https://rolz.org/api/?' + this.diceNumber + 'd12.json')
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

#TwelveSidedDieImg {
    width : 50px;
}
#d12mo {
    width : 30%;
}

</style>