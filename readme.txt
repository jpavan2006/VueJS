Anything in {{ will be passed in as java script.

directives are a way to connect js with html template elements.


v-if vs vshow
most times we will use v-if

v-show has element in dom.


app.component(name , options object)

events and methods with v-on directive.

var vs let vs const

1. custom components
2. composing components together.
3.importing components into another component.
4. props - passing data from parent to child
5.able to set data in parent by emit eent that parent listen and setting a value.

------

Life cycle hooks

beforeCreate
created
beforeMounted
mounted
beforeupdate
updated
beforeunmounted
unmounted

For testing hooks

1) create a custom component
   template:
      <div class="box"

   , 

        created(){

        }

        mounted(){

        }

        unmounted(){

        }


2)
<div id="app">
<button @click="togglebox" > ToggleBox </button>
<custom-box v-if"isVisible" />

3) let app=Vue.createApp(){

         data: function(){

                return{
                    isVisible: false
                }
          methods:

                togglebox: function() {
                  this.visible=!this.visible
		}
   }

Uses of hooks :

check if user is auth
get data from api calls
create /remve events.
-------


