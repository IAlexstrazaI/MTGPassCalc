<template>

  <h1>{{ msg }}</h1>
  <div class="col">
    <p>Сегодня: {{ Date(this.Today)  }}</p>
    <button @click="timeupdate"> Поставить сегодняшнюю дату  </button>
    <br>
    <br>
    <p>Дата окончания: {{ Date(this.EndDayMP) }}</p>
    <p>Максимум lvl: {{ this.MaxLvl }}</p>
    <br>
    <br>
    Current MP state
    <br>
    <br>
    Lvl MP:  <input @change = "SaveLocal('CurrentLevel',CurrentLevel)" v-model.number="CurrentLevel">
    <br>
    <br>
    Excess Mastery XP:  <input @change = "SaveLocal('ExcessMasteryExp',ExcessMasteryExp)" v-model.number="ExcessMasteryExp">
    <br>
    <br>
    Incomplete daily wins:  <input @change = "SaveLocal('IncompDW',IncompDW)" v-model.number="IncompDW">
    <br>
    <br>
    Incomplete daily quests:  <input @change = "SaveLocal('IncompDQ',IncompDQ)" v-model.number="IncompDQ">
    <br>
    <br>
    Incomplete weekly wins:  <input @change = "SaveLocal('IncompWW',IncompWW)" v-model.number="IncompWW">
    <br>
    <br>
    Expected mastery progression
    <br>
    <br>
    Daily wins per Day:  <input @change = "SaveLocal('DWperDay',DWperDay)" v-model.number="DWperDay">
    <br>
    <br>
    Daily quests left total:  <input @change = "SaveLocal('DQleft',DQleft)" v-model.number="DQleft">
    <br>
    <br>
    Weekly wins per week:  <input @change = "SaveLocal('WeeklyWinsPerWeek',WeeklyWinsPerWeek)" v-model.number="WeeklyWinsPerWeek">
  </div>
  <div class="col" ></div>
  <div></div>

  <grid-layout :layout.sync="layout"
               :col-num="12"
               :row-height="30"
               :is-draggable="draggable"
               :is-resizable="resizable"
               :vertical-compact="true"
               :use-css-transforms="true"
  >
    <grid-item v-for="item in layout"
               :static="item.static"
               :x="item.x"
               :y="item.y"
               :w="item.w"
               :h="item.h"
               :i="item.i"
    >
      <span class="text">{{itemTitle(item)}}</span>
    </grid-item>
  </grid-layout>
</template>
<script>

import VueGridLayout from 'vue-grid-layout';
window.addEventListener('beforeunload', () => {
console.log("Loaded!")
});

export default {
  components: {
    GridLayout: VueGridLayout.GridLayout,
    GridItem: VueGridLayout.GridItem
  },
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
      IncompDW: localStorage.getItem('IncompDW'),
      IncompDQ: localStorage.getItem('IncompDQ'),
      IncompWW: localStorage.getItem('IncompWW'),

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
 color:  #316e40 !important;
}

</style>
