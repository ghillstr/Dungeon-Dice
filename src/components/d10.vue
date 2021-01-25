<template>
<form>
    
    <tr id="dice">
        <td id="dice-type">d10</td>
        <td class="img"><img id="TenSidedDieImg" src="@/assets/10-sided-die.png" alt="10 Sided Die" v-on:click="diceRoll" ></td>
        <td><input id="numberOfDice" type="number" value="1" min="1" v-model.number="diceNumber"></td>
        <td><input type="number" id="d100mo" value="0" v-model.number="d10mo"></td> 
        <td><button id= "d10btn" type="button" v-on:click= "diceRoll">Roll</button></td>
        <td id="result">{{modifiedDice}}</td>
        <td id="details">{{details}}{{d10mo}}</td>
        </tr>
       
</form> 
</template>
<script>
import axios from 'axios';

export default {
    name: 'd10Value',
    data(){
        return {
            result : '0',
            diceNumber : '1',
            details: '',
            d10mo : '0',
            dNum : '1'

         }

    },
    computed:{
        modifiedDice() {
            let modDice = parseInt(this.result) + parseInt(this.d10mo) ;
             return modDice 
        }

    },
    

    methods:{
       diceRoll() {
            axios.get('https://rolz.org/api/?' + this.diceNumber + 'd10.json')
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

#TenSidedDieImg {
    width : 50px;
}

</style>