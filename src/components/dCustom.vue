<template>
<form>
    
    <tr id="customDice">
        <td id="dice-type">Custom</td>
        <td class="numberBox"><input id="userNumber" type="number" value="0" min="1" v-model.number="num"></td>
        <td><input id="numberOfDice" type="number" value="1" min="1" v-model.number="diceNumber"></td>     
        <td><input id="dCustomMo" type="number"   value="0" v-model.number="dMo"></td> 
        <td><button id= "dCustombtn" type="button" v-on:click= "diceRoll">Roll</button></td>
        <td id="result">{{modifiedDice}}</td>
        <td id="details">{{details}}{{dMo}}</td>
        </tr>
       
</form> 
</template>
<script>
import axios from 'axios'


export default {
    name: 'dCustomValue',
    data(){
        return {
            result : '0',
            details : '',
            dMo : '0',
            num : '1',
            diceNumber : '1'
         }

    },
    computed:{
        modifiedDice() {
            let modDice = parseInt(this.result) + parseInt(this.dMo) ;
             return modDice 
        }

    },
    

    methods:{
        diceRoll() {
            axios.get('https://rolz.org/api/?' + this.diceNumber + 'd' + this.num + '.json')
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

<style scoped>



#customDice td{
    width : 15%;
    padding: 0px;
    border: 1px none;
    padding-bottom : 40px;
}

#customDice .numberBox {    
    padding-left: 0%;
    padding-right: 10%;
    
}
#dCustomMo {
    width : 30%;
   
    
   
}

#numberOfDice {
    width : 30%;
    padding-right : 10px;
}

#userNumber {
    width : 150%;
    
    
}
#dCustombtn {
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
#dCustombtn:hover {
    background-color:lightskyblue;
    border: 2px solid blue;
    color: red;

}
@media screen  and (max-width: 600px){
    #dice-type-custom {
        font-size : 15px;
    }
    #dCustombtn {
    padding: 10px 10px;
    font-size: 18px;
}
#userNumber {
    width : 45px;   
}
#customDice .numberBox {    
    padding-right: 0%;   
}
#numberOfDice {
    width : 30%;
    padding-right : 10px;
}
}




</style>