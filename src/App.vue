<template>
    <div id="app">
        <div class="wrapper">
            <add 
                @add-item="addItem"
                @keydown="addItem($event.target.value)"/>
            <list :todos="todos" 
                @delete-item="deleteItem"/>
        </div>  
    </div> 
</template>


<script>
import list from './components/list.vue';
import add from './components/add.vue';

export default {
    name: "App",

    components: { add, list },

    data() {
        return {
            todos: []
        }
    },

    methods: {
        deleteItem(index) {
            this.todos.splice(index, 1)
        },

        addItem(text) {
            if (text.length) {
                if (text.length < 50) {
                    this.todos.push(text);
                } else {
                    alert('Hey, this note is too long')
                }
            }
            //else console.log("but you wrote nothing!")
        }
    }
}
</script>


<style lang="sass">
    #app
        width: 100%
        height: 100%

        display: flex
        justify-content: center
        align-items: center
</style>
