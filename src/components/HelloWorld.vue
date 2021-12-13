<template>

    <input v-model="display" readonly/>
    <div>
      
        <button @click="add('1')">1</button>     
     
             
        <button @click="add('2')">2</button>     
     
          
        <button @click="add('3')">3</button>        
     
          
        <button @click="add('+')">+</button>        
    </div>
   
    <div>
      
        <button @click="add('4')">4</button>     
     
             
        <button @click="add('5')">5</button>     
     
          
        <button @click="add('6')">6</button>        
     
          
        <button @click="add('-')">-</button>        
    </div>
   
    <div>
      
        <button @click="add('7')">7</button>     
     
             
        <button @click="add('8')">8</button>     
     
          
        <button @click="add('9')">9</button>        
     
          
        <button @click="add('*')">*</button>        
     
    </div>
    <div>
      
        <button @click="add('.')">.</button>     
     
             
        <button @click="add('0')">0</button>     
     
          
        <button @click="add('=')">=</button>        
     
          
        <button @click="add('/')">/</button>        
    </div>
       
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      display: '',
      op:'',
      store: 0,
      number:0,
      clean:false,
      myObect:{
        foo: 'bar'
      }
    }
  },
  methods: {
    add(value){
      if('='.includes(value)){
        switch(this.op){
          case '+':
            this.display = this.store + parseFloat(this.display) 
            break;
          case '-':
            this.display = this.store - parseFloat(this.display) 
            break;
          case '*':
            this.display = this.store - parseFloat(this.display) 
            break;
          case '/':
            this.display = this.store / parseFloat(this.display) 
            break;
        }
      }
      else if('+*-/'.includes(value)){
        this.op=value
        this.store=parseFloat(this.display)
        this.clean=true
      }
      else{
        if(this.clean){
          this.display=''
          this.clean=false
        }
        this.display +=value
      }
    }
  },
}
</script>


<style scoped>
  button{
    width: 2rem;
    height: 2rem;
  }
  input {
    margin-bottom: 1rem;
    width: 50vw;
    font-size: 1.5rem;
    text-align: right;
  }
</style>
