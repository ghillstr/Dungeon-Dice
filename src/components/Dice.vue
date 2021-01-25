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
          <td>Details<ul>(dice) & modifer</ul></td>
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
ul {
    font-size : 20px;
    
}
#dieNumber{
    padding-left: 170px;
}

</style>