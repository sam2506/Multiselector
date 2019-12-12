<template>
    <div>
        <h3>Expertise Multiselector</h3>
        <hr>
        <div class="divn d-inline" v-bind:key="skill.id" v-for="skill in skills">
            <b-button class="butn" v-on:click="$emit('inv-Select',skill.id)" v-bind:pressed="skill.selected" size="sm" variant="outline-primary">{{skill.name}}</b-button>
        </div>
        <br><br>
    </div>
</template>

<script>

export default {
    name: 'Commonskills',
    props: ["skills"],
}
</script>

<style scoped>
    .divn{
        margin: 5px;
    }
    .butn{
        font-size: 13px;
        margin-bottom: 5px;
    }
</style>