<template>
    <div id="app">
        <div class="wrapper">
            <header>
                <h1>ToDo <span>App</span></h1>
            </header>
            <add @add-item="addItem"/>
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
            /*if (text.length) {
                if (text.length < 50) {
                    this.todos.push(text);
                } else {
                    alert('Hey, this note is too long')
                }
            }*/
            this.todos.push(text);
            //else console.log("but you wrote nothing!")
        }
    }
}
</script>


<style lang="sass">
    @import './assets/style.sass'

    #app
        width: 100%
        height: 100%

        display: flex
        justify-content: center
        align-items: center

    .wrapper
        display: flex
        flex-direction: column
        align-items: flex-start

    header
        width: 100%
        display: flex
        justify-content: center

    h1
        font-family: 'Roboto'
        color: $black
        font-size: 36px
        font-weight: 500

        span
            color: $green
</style>
