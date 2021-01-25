<template>
<form>
    
    <tr id="dice">
        <td id="dice-type">d100</td>
        <td class="img"><img id="oneHundredSidedDieImg" src="@/assets/100-sided-die.jpg" alt="100 Sided Die" v-on:click="diceRoll" ></td>
        <td><input id="numberOfDice" type="number" value="1" min="1" v-model.number="diceNumber"></td> 
        <td><input type="number" id="d100mo" value="0" v-model.number="d100mo"></td> 
        <td><button id= "d100btn" type="button" v-on:click= "diceRoll">Roll</button></td>
        <td id="result">{{modifiedDice}}</td>
        <td id="details">{{details}}{{dMo}}</td>
        </tr>
       
</form> 
</template>
<script>
import axios from 'axios';

export default {
    name: 'd100Value',
    data(){
        return {
            result :  '0',
            diceNumber : '1',
            details : '0',
            d100mo : '0',
         }

    },
    computed:{
        modifiedDice() {
            let modDice = parseInt(this.result) + parseInt(this.d100mo) ;
             return modDice 
        }

    },
    

    methods:{
       diceRoll() {
            axios.get('https://rolz.org/api/?' + this.diceNumber + 'd100.json')
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

#oneHundredSidedDieImg {
    width : 50px;
}
#d100mo {
    width : 30%;
}

</style>