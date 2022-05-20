<template lang="">

    <div>
    <div  id="editor" @keyup="render()"></div>
    <iframe id="iframe" style="border-style: solid;border-width: thin;" 
      frameBorder="0" width="464" height="460" src="test.html">
     <span id="output"></span>

    </iframe>
        
    </div>
</template>
<script>

import * as CodeMirror from 'codemirror';
import 'codemirror/lib/codemirror.css';
import 'codemirror/theme/dracula.css';
import 'codemirror/mode/javascript/javascript.js';


export default {
    name:'CodeMirror',
   
    data(){
        return{
            content:'let x=0',
            cmInstance:'',
            returnval:'x',
           
        }
    },
    
    mounted(){
       this.cmInstance = CodeMirror(document.querySelector('#editor'),{
            lineNumbers:true,
            theme:'dracula',
            value:'let x',
            mode:'javascript'
        }).setSize(700,300);

     console.log(this.cmInstance.getValue())
      
      
    },  
    methods:{
        render:function(){
         
        
             document.getElementById("iframe").src = "test.html";

        }
    }
    
}
</script>
<style lang="">
    
</style>