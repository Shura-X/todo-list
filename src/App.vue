<template>
    <div id="app">
        <div class="wrapper">
            <header>
                <h1>ToDo <span>App</span></h1>
            </header>
            <add @add-item="addItem"/>
            <list :todos="todos"
                @remove-item="removeItem"/>
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
            todos: [],
            curr_index: 0 //index of the last item + one
            //to assign 'number' value to the new item
        }
    },

    methods: {
        //here the method receives the 'id' of the item
        //to remove and detects this item by the prop 
        removeItem(index) {
            this.todos = this.todos.filter(item => {
                return index != item.id
            })

            //now we check if the list is empty, and then
            //reset this.curr_indext if it is
            if (!this.todos.length) {
                this.curr_index = 0;
            }

            //console.log(this.curr_index);
            //console.log('todos length: ', this.todos.length);
        },

        addItem(text) {
            this.todos.push({
                //push new item, we increase the 'id' of the next item
                id: this.curr_index++,
                message: text
            });

            //console.log(this.curr_index);
            //console.log('todos length: ', this.todos.length);
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

    .list-enter-active,
    .list-leave-active
        transition: all 1s

    .list-enter,
    .list-leave-to
        opacity: 0
</style>
