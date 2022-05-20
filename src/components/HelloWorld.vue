<template>
 <div>
   <nav class="navbar bg-light">
  <div class="container-fluid">
    <span class="navbar-brand mb-0 h1">magmaGo</span>
  </div>
</nav><br><br>
   <div  class="container row">
     <div class="col-6">
          <codemirror
          v-model="code"
          placeholder="Code gose here..."
          :style="{ height: '400px', width: '500px' }"
          :autofocus="true"
          :indent-with-tab="true"
          :tabSize="2"
          :extensions="extensions"
          @ready="log('ready', $event)"
          @change="log('change', $event)"
          @focus="log('focus', $event)"
          @blur="log('blur', $event)"
          @keyup="render"
        />
          </div>
      <div class="col-6">
          
        <iframe id="iframe" style="border-style: solid;border-width: thin;" 
            frameBorder="0" width="464" height="460" src="test.html">
          <span id="output"></span>

          </iframe>

      </div>

   </div>
   

    </div>
</template>



<script>
  import { Codemirror } from 'vue-codemirror'
  import { javascript } from '@codemirror/lang-javascript'
  import { oneDark } from '@codemirror/theme-one-dark'
  import { ref } from 'vue'


  export default {
    name:'HelloWorld',
    components: {
      Codemirror
    },
    setup() {
      const code = ref(`console.log('Hello, world!')`)
      const extensions = [javascript(), oneDark]

      return {
        code,
        extensions,
        log: console.log
      }
    },
    methods:{
      render(){
        // alert(this.code);
         localStorage.setItem("code",this.code);
         document.getElementById("iframe").src = "test.html";
      }
    }
  }
</script>

