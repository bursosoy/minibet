<style scoped>

.tabs-wrap {
    min-height: 3rem;
    display: flex;
    flex-direction: row;
    align-items: center;
    padding: 0rem 1.5rem;
    white-space: nowrap;
    overflow: auto;
}

.tabs-active {
    background-color: #ddd;
    transition-property: background-color, border-radius;
    transition-duration: 0.15s, 0.2s;
    transition-timing-function: ease-in;
    margin-right: 0.5rem;
    min-width: 3rem;
    min-height: 3rem;
    text-align: center;
    padding: 0rem 2rem;
    border-radius: 1.5rem 1.5rem 1.5rem 0;
    font-weight: bold;
    color: #111;
    cursor: pointer;
}

.tabs-active:hover{
  background-color: #eee;
  border-radius: 1.5rem 0rem 1.5rem 1.5rem;
}

.tabs-inactive {
    background-color: #111;
    transition-property: background-color, border-radius;
    transition-duration: 0.15s, 0.2s;
    transition-timing-function: ease-in;
    margin-right: 0.5rem;
    min-width: 3rem;
    min-height: 3rem;
    text-align: center;
    padding: 0rem 2rem;
    border-radius: 1.5rem 1.5rem 1.5rem 0;
    font-weight: bold;
    color: #AAA;
    cursor: pointer;
}

.tabs-inactive:hover{
  background-color: #000;
  border-radius: 1.5rem 0rem 1.5rem 1.5rem;
}

.text-salmon{
  color: salmon;
}
</style>

<template>

<div class="tabs-wrap" style="margin-top: 3rem">
  <div v-for="tab in tabs" :key="tab.id" :class="[{'tabs-active': tab.isActive, 'tabs-inactive': !tab.isActive},{'text-salmon' : !tab.isActive && 2<1}]" :style="tab.style" class="flex-dead-center" @click="tabClicked(tab,'anthony',40)">{{tab.label}}</div>
</div>

</template>

<script>

export default {
    name: 'Tabs',
    data() { // variable declarations
        return {
          tabs: [
            {id: 0, label: 'For Me', isActive: true},
            {id: 1, label: 'Matches', isActive: false},
            {id: 2, label: 'Trending Games', isActive: false, style:{'min-width':'110px'}},
            {id: 3, label: 'Top Rated', isActive: false, style:{'min-width':'80px'}}
          ]
        }
    },
    methods:{
      tabClicked(object,name,age){
        this.$emit('tabClickedEvent',object,name,age)// passing the whole object onto the parent vue where the component is loaded
      }
    }
}

</script>
