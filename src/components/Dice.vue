<template>
<header>
  <h1 id=headline>Dungeon Dice</h1>
  <div id="titles">
      <tr>
          <td class="Die">Die</td>
          <td id="dieNumber">Number of Dice</td>
          <td>Modifer (+/-)</td>
          <td>Roll</td>
          <td>Results</td>
          <td>Details<span> (dice) & modifer</span></td>
      </tr>
    </div>
 </header>
   
</template>

<script>

export default {
    name: 'Dice',
   
    }

</script>

<style>

#headline {
    padding-top: 40px;
    font-size: 60px;
    font-style: italic;
    color:white;
    align-content: center;
    -webkit-text-stroke-width: 4px;
    -webkit-text-stroke-color: #12460b;
}

#titles{ 
    margin-left: 200px;
    font-size: 40px;
    
}
#titles .Die {
    padding-left: 25px;
    padding-right: 150px;
}

#titles td {
    width: 5%;
    padding : 0px;
    padding-bottom: 20px;
    padding-left: 80px;
   
}
span{
    font-size : 20px;
    display: inline-block;
    text-align: center;
    
    
}
#dieNumber{
    padding-left: 170px;
}
@media  screen and (max-width: 600px) {
    #headline {
    padding-top: 40px;
    padding-bottom: 40px;
    font-size: 40px;
    }
     #titles{
         margin-left : 0px;
         font-size : 18px;
         padding-bottom: 30px;
         padding-left: 0px;
}
    span {
        font-size :10px;
    }
    #titles .Die {
        padding-left: 0px;
        padding-right: 0px;
}   
    #titles td {
        width: 0%;
        padding : 0px;
        padding-bottom: 20px;
            padding-left: 8px;
   
}

    
}
</style>