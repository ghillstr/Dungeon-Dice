<template>
<form>
    
    <tr id="dice">
        <td id="dice-type">d20</td>
        <td class="img"><img id="TwentySidedDieImg" src="@/assets/twenty-sided-dice-md.png" alt="20 Sided Die" v-on:click="diceRoll" ></td>
        <td><input id="numberOfDice" type="number" value="1" min="1" v-model.number="diceNumber"></td> 
        <td><input type="number" id="d20mo" value="0" v-model.number="d20mo"></td> 
        <td><button id= "d20btn" type="button" v-on:click= "diceRoll">Roll</button></td>
        <td id="result">{{modifiedDice}}</td>
        <td id="details">{{details}}{{d20mo}}</td>
        </tr>
       
</form> 
</template>
<script>
import axios from 'axios';

export default {
    name: 'd20Value',
    data(){
        return {
            result : '0',
            diceNumber : '1',
            details: '',
            d20mo : '0',
            dNum : '1'

         }

    },
    computed:{
        modifiedDice() {
            let modDice = parseInt(this.result) + parseInt(this.d20mo) ;
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

#dice-type{
    font-size: 32px;
    
}
 #dice .img {
    width : 0%;
    padding-left: 0%;
    padding-right: 11%;

}

img {
    width : 50px;
    border: 4px solid transparent;
    border-radius: 8px;
   
}
img:hover {
    border: 4px solid gold;
    border-radius: 8px;
}
#numberOfDice {
    width : 30%;
}

form {
    margin-left : 100px;
}

#dice td{
    width : 15%;
    padding-bottom: 30px;
    padding-left: 15px;
    border: 1px none;
        
    
}
#d20mo {
    width : 30%;
}
input {
    border: 2px solid blue;
    border-radius: 4px;
    padding: 12px 10px;
}
button {
    background-color: #4237da;;
    border: 2px solid transparent;
    color: white;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    border-radius: 4px;
    padding: 10px 32px;
    font-size: 24px;
}

button:hover {
    background-color:lightskyblue;
    border: 2px solid blue;
    color: red;

}
#result {
    font-size: 32px;
}
@media screen  and (max-width: 600px) {

    form {
    margin-left : 0px;
}
#dice-type{
    font-size: 18px;
    
}
 #dice .img {
     display: none;
    width : 0%;
    padding-left: 0%;
    padding-right: 0%;

}

#dice td{
    width : 5=10%;
    padding-bottom: 20px;
    padding-left: 5px;
    
}
button {
    
    padding: 10px 10px;
    font-size: 18px;
}
    
}




</style>