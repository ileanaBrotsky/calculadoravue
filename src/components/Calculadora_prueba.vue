<template>
<body>
  
  <h2>calculadora</h2>
  <div class="card">  
    <p class="visor">{{visor}}</p>
   
           <hr> 
    <div class="botonera">
              <button class='borrar' @click="borrar()">borrar</button>
              <button @click="haceCuentaPorcentaje(' % ')">%</button>
            
              
            
              <button @click="haceCuenta(' / ')">/</button>
            
              <button @click="haceCuenta('7')">7</button>
             
              <button @click="haceCuenta('8')">8</button>
              <button @click="haceCuenta('9')">9</button>
              <button @click="haceCuenta(' * ')">*</button>
              <button @click="haceCuenta('4')">4</button>
              <button @click="haceCuenta('5')">5</button>
              <button @click="haceCuenta('6')">6</button>
              <button @click="haceCuenta(' - ')">-</button>
              <button @click="haceCuenta('1')">1</button>
              <button @click="haceCuenta('2')">2</button>
              <button @click="haceCuenta('3')">3</button>
               <button @click="haceCuenta(' + ')">+</button>
              <button  class='cero' @click="haceCuenta('0')">0</button>
             
              <button @click="haceCuenta('.')">,</button>
             
              <button @click="haceCuenta(' =')">=</button>
             
             
            
            
            
     </div>
      

   </div> 
   </body>
</template>

<script>
 import { ref } from "vue";
export default {
    setup(){
    let visor= ref('');
   
    
    
    const tomarValor=(valor)=>{
    visor.value=visor.value +valor;
    
    }

    const haceCuenta=(valor)=>{
      visor.value=visor.value +valor;
     
        let editor =  visor.value.split(' ') ;
     
       if(editor.length>3){
         let num1=Number(editor[0]);
          let signo=editor[1];
          let num2=Number(editor[2]);
          let resultado= eval(num1+ signo + num2);
          if(valor===" ="){
          visor.value= resultado;
          }
          else{
           visor.value= resultado + valor;
           
            }
       }
        }
    const haceCuentaPorcentaje=(valor)=>{
        visor.value=visor.value +valor;
     
        let editor =  visor.value.split(' ') ;
        console.log(editor);
        if (valor===' % '){
          if(editor.length>3){
            let num1=Number(editor[0]);
              let signo=editor[1];
              let num2=Number(editor[2]);
            
                 let porcentaje= (num1*num2/100);
                 if(signo=== '*'){
                   porcentaje= (num2/100);
                 }
                let resultado= eval(num1+ signo + porcentaje);
             
                if(valor===" ="){
                visor.value= resultado;
                }
                else{
                visor.value= resultado + valor;
                }
           }
          }
        }
    
    const borrar=()=>{
      visor.value= '';
    }
        return{
          visor,
          tomarValor,
          haceCuenta,
          haceCuentaPorcentaje,
          borrar,
        };
  },

};
</script>

<style>
body{
    margin:0;
    padding: 0;
    font-family: monospace;
    box-sizing: border-box;
}
h2{
    color:rgb(230, 242, 242);
    text-align: center;
    margin-bottom: 20px;
    font-size: 30px;
}
.card{
  width: 250px;
   min-width: 250px;
    margin:auto;
    background: rgba(166, 176, 155, 0.6);
    padding:20px;
    /*para que el padding no se agregue al ancho establecido sino que se cuente hacia adentro*/
    border-radius: 5px;
    display: flex;
    flex-direction: column;
    justify-content: center;
}
.visor{
  margin: auto;
  border: solid 1px;
  padding:10px;
  height: 20px;
  background: white;
  border-radius: 5px;
   width: 200px;
}
hr{
  margin-top:20px;
  width: 210px;

  border: black solid 1px;
}
.cero, .borrar{
width: 110px;
}

.borrar{

  font-size: 12px;
}

.botonera{
  margin: 5px auto;
 width: 250px;
  display: flex;
  flex-wrap: wrap;
  gap: 5px;
    justify-content: center;
  
}
button{
  min-width: 50px;
    padding:10px;
    font-size: 17px;
    background:rgb(51, 59, 56);
    color:aquamarine;
}
button:hover{
  color:rgb(51, 59, 56);
   background:aquamarine;
}

/*para que sea responsive, si el máx es hasta 480px en este caso, se va a realizar lo que está a continuación
si se pasa de ese tamaño, no se cumple lo que sigue*/
@media(max-width:480px){

    .card{
            width:100%;
        }
}

</style>