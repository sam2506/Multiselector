<template>
  <div id="app">
    <b-container class="bv-example-row">
      <b-row>
        <b-col lg="6" offset="3">
          <Commonskills v-on:inv-Select="invertSelect" v-bind:skills="skills"/>
          <Addskill 
          v-on:select-skill="selectSkill"
          v-on:del-skill="invertSelect" v-bind:skills="skills"/><br>
          <b-button v-on:click="submit" variant="success">Submit</b-button>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Commonskills from './components/Commonskills.vue'
import Addskill from './components/Addskill.vue'

export default {
  name: 'app',
  components: {
    Commonskills,
    Addskill
  },
  methods: {
    invertSelect(skillId){
      var allSkills = this.skills;
      for(var x in allSkills){
        if(allSkills[x].id == skillId){
          allSkills[x].selected = !(allSkills[x].selected);
        }
      }
    },
    submit(){
      var allSkills = this.skills;
      for(var x in allSkills){
        allSkills[x].selected = false;
      }
    },
    selectSkill(skillId,callback){
      var allSkills = this.skills;
      for(var x in allSkills){
        if(allSkills[x].id == skillId){
          allSkills[x].selected = true;
        }
      }
      callback();
    }
  },
  data() {
    return {
      skills:[{id: 1,name: "JavaScript",selected: false},
        {id: 2,name: "WebDesign",selected: false},
        {id: 3,name: "HTML",selected: false},
        {id: 4,name: "CSS",selected: false},
        {id: 5,name: "Programming",selected: false},
        {id: 6,name: "Adobe Photoshop",selected: false},
        {id: 7,name: "MS Excel",selected: false},
        {id: 8,name: "Networking",selected: false},
        {id: 9,name: "C++",selected: false},
        {id: 10,name: "Python",selected: false},
        {id: 11,name: "Java",selected: false}
      ]
    }
  }
}
</script>

<style>
  #app{
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    margin-top: 60px;
  }
</style>

