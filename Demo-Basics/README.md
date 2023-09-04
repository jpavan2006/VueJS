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