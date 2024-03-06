<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>Сегодня: {{ this.Today }}</p>
    <button @click="timeupdate"> Поставить сегодняшнюю дату  </button>
    <br>
    <br>
    <p>Дата окончания: {{ this.EndDayMP }}</p>

    <br>
    <br>
    Current MP
    <br>
    <br>
    Lvl MP:  <input @change = "SaveLocal('CurrentLevel',CurrentLevel)" v-model.number="CurrentLevel">
    <br>
    <br>
    Excess Mastery XP:  <input @change = "SaveLocal('ExcessMasteryExp',ExcessMasteryExp)" v-model.number="ExcessMasteryExp">
  </div>
</template>
<script>
window.addEventListener('beforeunload', () => {
console.log("Loaded!")
});

export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  data(){
    return{

      /* Basics */
      Today: localStorage.getItem('Today'),
      EndDayMP: 1713240215,
      MaxLvl: 70,

      /* Current MP */
      CurrentLevel: localStorage.getItem('CurrentLevel'),
      ExcessMasteryExp: localStorage.getItem('ExcessMasteryExp'),
      IcompDW: localStorage.getItem('IncompDW'),
      IcompDQ: localStorage.getItem('IncompDQ'),
      IcompWW: localStorage.getItem('IncompWW'),

      /* Expected mastery progression */
      DWperDay: localStorage.getItem('DWperDay'),
      DQleft: localStorage.getItem('DQleft'),
      WeeklyWinsPerWeek: localStorage.getItem('WeeklyWinsPerWeek'),

    }
  },
  methods:{
    timeupdate: function (){
      localStorage.setItem('Today',Date.now())
      this.Today = localStorage.getItem('Today');
    },
    SaveLocal: function(key,value){
      localStorage.setItem(key,value);
      this.key = localStorage.getItem(key);
    }

  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
h1{
 color:  #316e40   ;
}

</style>
