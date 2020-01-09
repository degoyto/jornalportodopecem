<template>
  <div class="container">
    <div class= "caixa" v-for="noticia in noticias" :key="noticia.id"  >
      <div class="img" v-bind:style="{ backgroundImage: 'url(' + noticia.fotoUrl + ')' }"></div>
      
      <div class="info">
        <div class="itens">
          <h1  >{{noticia.title}}</h1>
          <div class="tipo">
            {{noticia.tipo}}
            
          </div>
          
          <div class="autor"> 
            Autor: {{noticia.autor}}
            
          </div>
          
          <div class="conteudo" >
            
            <p>{{noticia.conteudo}}</p>
          </div>
          <div class="data">
            {{noticia.createdAt | formatDate}}
          </div> 
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Logo from '~/components/Logo.vue';


export default {
  components: {
    Logo,
  },
  data () {
    return {
      noticias:null
    }
    
  },
  async created() {
    try {
      const res = await axios.get(`https://dev-aileron-262703.appspot.com/gnoticias`)
      this.noticias=res.data;
      console.log(res.data);
      
    }
    catch (error) {
      console.log(error)
    }
  }
}
</script>

<style>
.caixa{
    width:80%;
    margin-top:2%;
    margin-bottom:2%;
    box-shadow: 2px 2px 2px rgba(0,0,0,0.3);
    margin-left:5%;
    height:40vh;
    min-height:300px;
  }
 
  .info{
    width:50%;
    float:right;
    padding-left:2%;
    padding-right: 2%;
    text-align: left;
  }
  .info p{
    margin-top: 5px;
    font-size:1vw;

  }
  .info h1{
    font-size:2.6vw;
    margin-bottom: -3px;
    
  }
  .tipo, .autor{
    font-size:0.7vw; 
  }
  .botao{
    margin-top:-25px;
    background-color:#142248;
    border: #142248;
    float:right;
    font-size:0.8vw; 
    width:20%;
  }
  .data{
    font-size: 0.8vw;
    margin-top:20px;
  }
  .tipo{
    width:80px;
    background-color:#142248;
    color:white;
    text-align: center;
  }
  .img{
    width:38vw;
    height: 40vh;
    min-height:300px;
    float:left;
    background-repeat: no-repeat;
    background-size: cover;
    
    
  }
</style>
