<template>
    <div>
        <div class="divbox">
            <div class="divn d-inline" v-bind:key="skill.id" v-for="skill in skills">
                <b-button :class="[skill.selected ? '' : 'd-none']" class="butn"  
                    v-bind:pressed="true" size="sm" variant="outline-primary">
                    {{skill.name}}
                    <span v-on:click="$emit('del-skill',skill.id)" class="cross" aria-hidden="true">×</span>
                </b-button>
            </div>
            <input v-on:input="textEntered" v-model="skillEntered" type="text" placeholder="Enter skill to be added">
        </div>
        <b-list-group class="listgroup" :class="[display ? '' : 'd-none']">
            <div v-bind:key="skill.id" v-for="skill in skills">
                <b-list-group-item 
                    class="list"
                    :class="[skill.name.toLowerCase().search(skillEntered.toLowerCase()) !==-1 ? '' : 'd-none']"
                    v-on:click="selectSkill(skill)">
                    {{skill.name}}
                </b-list-group-item>
            </div>
        </b-list-group>
    </div>
</template>

<script>
export default {
    name: 'Addskill',
    props: ["skills"],
    data(){
        return{
            skillEntered: '',
            display: false
        }
    },
    methods: {
        textEntered(){
            const text=this.skillEntered;
            if(text !== ''){
                this.display = true
            }
            else{
                this.display = false
            }
        },
        selectSkill(skill){
            var that=this;
            this.$emit('select-skill',skill.id,function(){
                that.skillEntered="";
                that.textEntered();
            })
        },
    }
}
</script>

<style scoped>
    .listgroup{
        max-height: 250px;
        overflow: hidden;
    }
    .list:hover{
        background-color: #0275d8;
        cursor: pointer;
    }
    .divbox{
        border-style: solid;
        border-width: 1px;
        overflow: hidden;
    }
    input{
        border: none;
        max-width: 100%;
        text-align: center;
    }
    input:focus, textarea:focus, select:focus{
        outline: none;
    }
    .butn{
        cursor: default;
        font-size: 10px;
    }
    .cross{
        cursor: pointer;
    }
    .divn{
        margin: 1px;
    }
</style>
