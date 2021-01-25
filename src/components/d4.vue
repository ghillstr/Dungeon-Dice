<template>
<form>
    
    <tr id="dice">
        <td id="dice-type">d4</td>
        <td class="img"><img id="FourSidedDieImg" src="@/assets/4-sided-die.png" alt="4 Sided Die" v-on:click="diceRoll" ></td>
        <td><input id="numberOfDice" type="number" value="1" min="1" v-model.number="diceNumber"></td>
        <td><input type="number" id="d4mo" value="0" v-model.number="d4mo"></td> 
        <td><button id= "d4btn" type="button" v-on:click= "diceRoll">Roll</button></td>
        <td id="result">{{modifiedDice}}</td>
        <td id="details">{{details}}{{d4mo}}</td>
        </tr>
       
</form> 
</template>
<script>
import axios from 'axios';

export default {
    name: 'd4Value',
    data(){
        return {
            result : '0',
            diceNumber : '1',
            details: '',
            d4mo : '0',
            dNum : '1'

         }

    },
    computed:{
        modifiedDice() {
            let modDice = parseInt(this.result) + parseInt(this.d4mo) ;
             return modDice 
        }

    },
    

    methods:{
       diceRoll() {
            axios.get('https://rolz.org/api/?' + this.diceNumber + 'd4.json')
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

#FourSidedDieImg {
    width : 50px;
}
#d4mo {
    width : 30%;
}

</style>