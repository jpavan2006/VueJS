# VueJS

--------------

index1.html observations :

1. Connect javascript and html dom elements
2. v-model used to get hold of input in input text
   Additionally defining v-model passes modelValue as prop to child component from parent component.
3.v-if , v-else-if , v-else , v-show , v-on represented as shortcut @
4. CDN that lets us write a simple vue js program.
5. Vue.createApp creates a default component.
6. Observe how data is initialized in default component.
7. Observe the {{ usage.

Observations on output image and tests :
1. abc entered in text box is automatically populated to string.
2.Toggle box works based on directives logic defined.

------------
index2.html observations :

1. v-cloak directive introduced to control display on component to address glit or latency.
2. multiple divs in html
3. created a custom parent component with name - login-form
4. controlling the default submit behaviour through @submit.prevent which is the v-on directive.
5. Can also observe the difference between default component and custom component.
6. template and form  ; data() ; methods 
7. handleSubmit method - how we got the email and password and displayed in console.


------------
index3.html observations :

1. introduced css input
2. created custom-input component which can be used in login-form component.
3. parent component :
		1.see title is coming from data. js and html elements are connecting this way with {{
		2. <custom-input type="email" v-model="email" v-bind:label="emailLabel" />
		
	        v-model email so that u r getting hold of this value and passing to child as modelValue prop.
			v-bind:label="emailLabel" - you are assigning emailLabel value from data to lable
			                          - you are vbind lable so that it is availble to child component as prop.
	 
        3. components: ['custom-input']
               - you are telling parent component that it will be using a child component called custom-input
	    4. what is defined in data can be used with in template. data is connection bw template and JS .
		
		        data() {
                return {
                    title: 'Login Form',
                    email: 'kk',   // this is default value assinged to vmodel value in template - email
                    password: 'kkk',
                    emailLabel: 'Email',
                    passwordLabel: 'Password'
                }
              },
			  
		5.handleSubmit method - how we got the email and password and displayed in console.
		
		     methods: {
                handleSubmit(){
                    console.log('submitted')
                    console.log(this.email,this.password)
                    
                }
              }
4.child component:
       1. observe syntax of creating component.
	       app.component('custom-input', {
		
		2. observe label ,modelValue coming from parent as prop to child.
		   observe how vmodel on textbox  inputValue for computing purpose .
		
            template: `
                <label>
                   {{ label }}       
                   <input type="text" v-model="inputValue" />
                </label>
               
            `,
            props: ['label', 'modelValue'],
			
		3. computed is a way of child emitting event which  parent can listen when value changes.
		   v-model frm parent is listening to child component update.
		   
            computed: {
               inputValue: {
                get(){
                     return this.modelValue
                },
                set(value){
                    console.log(value)
                    this.$emit('update:modelValue' , value)
                    //first param is type of event  emitting and second is the value u r setting.
                    //lets u emit events that other components can listen to.
                    //the props which we pass to child cant be changed in child.
					 //first param is type of event iam emitting and second is the value u r setting.
                    //lets u emit events that other components can listen to.
                    //v-model frm parent is listening to child component update.

                   
                }
               }
            }
         }
         
         )

------------
index4.html observations :

parent componet:
		1. observe that we introduced inputs json data.
						data() {
						return {
							title: 'Login Form',
							inputs: [
								{

									label: 'Email' ,
									value: '',
									type: 'email'
								},
								{
									label: 'Password',
									value: '',
									type: 'password'

								}
							  
							],
							email: 'kk',
							password: 'kkk',
							emailLabel: 'Email',
							passwordLabel: 'Password'
						}
					  },
					  
		2. In handleSubmit method , we are getting values from inputs
			   methods: {
						handleSubmit(){
							console.log('submitted')
							console.log(this.inputs[0].value , this.inputs[1].value)
							
						}
					  }
					  
		3. watch how v-for is working
							<p v-for="(str,i) in inputs" :key="i"> {{ i }} </p>  //0 , 1
							<p v-for="(str,i) in inputs" :key="i"> {{ str }} </p> 
							//  { "label": "Email", "value": "", "type": "email" }
							//  { "label": "Password", "value": "", "type": "password" }
							
		4. including child component in parent through v-for
			   <custom-input 
				   v-for="(input, i) in inputs"
				   :key="i"
				   v-model="input.value"
				   :label="input.label"
				   :type="input.type"
				/>
		
child component :

      1.  we ve  v-bind type , label in parent and hence availble as props.
	  
	       app.component('custom-input', {
            template: `
                <label>
                   {{ label }}       
                   <input :type="type" v-model="inputValue" /> // every key that u enter is set  to parent through computed.
                </label>
               
            `,
            props: ['label', 'type','modelValue'],  // props are values coming from parent to child
			
			** vbind type in child - not sure if it has any meaning to do so.
			
------------
index5.html observations :

ref() can store primitive values, while reactive() cannot.

Calling reactive(0) with a primitive value is incorrect. Don't do this. If you need to make reactive primitive values, ref(0) is the way to go.

The reason why reactive() works only with objects is in Vue's reactivity implementation. Vue uses Proxies to intercept property changes on objects. And proxies do not work with primitives.

Nevertheless, reactive({ count: 0}) initialized with an object is perfectly valid and creates a reactive object.


import { ref } from 'vue'

const numberRef = ref(0);
console.log(numberRef.value); // logs 0

const objectRef = ref({ count: 0 })
console.log(objectRef.value.count); // logs 0

default component
data()
 count: Vue.ref(0)
 
 html:
 
 <button @click="count++">
 Count is: {{ count }}
 </button>