<template>
  <div class="container-flex" >
    
    <div class="container cabecalho ">
      <!-- Aqui fica os itens acima da logo, como data e redes sociais -->
      <div class="acima">
        <p class="data">Pecém,  {{ date() }}</p> 
        <div class="sociais">
          <font-awesome-icon :icon="{ prefix: 'fab', iconName: 'facebook' }"/>
          <font-awesome-icon :icon="{ prefix: 'fab', iconName: 'instagram' }"/>
        </div>
        
      </div>
      <!-- Aqui se encontra a logo e o anuncio do cabeçalho -->
      <div class="abaixo">
        <img @click="navigateTu()" class="logo" src="../assets/logo.svg">
        <anuncio class="anuncio"></anuncio>
      </div> 
    </div>

    <div class="container-flex back  ">
      <div class="container">
        <!-- menu -->
        <b-navbar toggleable="lg"  type="dark" class="barra " >
      

          <b-navbar-toggle target="nav-collapse" class="botao"></b-navbar-toggle>
          <!-- Itens do menu -->
          <b-collapse id="nav-collapse" class="menu" is-nav >
            <!-- Esse aparece na versão pc -->
            <ul class="pc">
              
              <li><a href="#/noticias/destaques" @click="navigateTo()">destaques portuários</a></li>
            
              <li class="noticias-btn"><a href="#/noticias/noticias" @click="navigateTo()">Notícias</a>
                      <ul>
                            <li><a href="#/noticias/nacionais" @click="navigateTo()">Nacionais</a></li>
                            
                            <li><a href="#/noticias/internacionais" @click="navigateTo()">Internacionais</a></li>
                                          
                      </ul>
                  </li>
              
              <li><a href="#/noticias/artigos" @click="navigateTo()">Artigos e Opinião</a></li>
              
              <li><a href="#/noticias/turismo" @click="navigateTo()"> turismo</a></li>

              <li><a href="#/noticias/comex" @click="navigateTo()">Comércio exterior</a></li>
              <li><a href="#/noticias/logistica" @click="navigateTo()">logística e transporte</a></li>
              <li><a href="#/noticias/entrevistas" @click="navigateTo()">entrevistas</a></li> 
              <li><a href="#/noticias/portos" @click="navigateTo()">Portos do Brasil</a></li>
              <li><a href="#/noticias/eventos" @click="navigateTo()">Eventos</a></li>
                                              
                      
                  
            </ul>
            <!-- Esse so aparece na versão mobile -->
            <ul class="cel">
              
              <li><a href="#/noticias/destaques" >destaques portuários</a></li>
              
              <li><a href="#/noticias/nacionais" >Nacionais</a></li>
                            
              <li><a href="#/noticias/internacionais" >Internacionais</a></li>
              
              <li><a href="#/noticias/artigos" >Artigos e Opinião</a></li>
              
              <li><a href="#/noticias/turismo" > turismo</a></li>

              <li><a href="#/noticias/comex" >Comércio exterior</a></li>
              <li><a href="#/noticias/logistica" >logística e transporte</a></li>
              <li><a href="#/noticias/entrevistas" >entrevistas</a></li> 
              <li><a href="#/noticias/portos" >Portos do Brasil</a></li>
              <li><a href="#/noticias/eventos" >Eventos</a></li>
                                                   
            </ul>

          <!-- Right aligned nav items -->
          <!-- inicio do navbar que deixa o "pesquise" do celular ok-->
            <b-navbar-nav class="ml-auto">
              <!-- <b-nav-form class="pesquise">
                <b-form-input size="sm" class="mr-sm-2" v-model="itemPesquisado"  placeholder="Pesquise"></b-form-input>
                <b-button size="sm" class="my-2 my-sm-0 btn-pesquisa" >Pesquise</b-button>
              </b-nav-form> -->
            </b-navbar-nav>
          </b-collapse>
        </b-navbar><!-- fim do menu -->

        <!-- Barra de pesquisa versão Pc -->
        <div class="pesquisa">
          <b-form-input size="sm" class="mr-sm-1 pesquisa-input" v-model="itemPesquisado" placeholder="Pesquise" style="margin-top:7px;"></b-form-input>
          <div>
            <b-button size="sm" class="my-2 my-sm-0 btn-pesquisa" >Pesquise</b-button>

          </div>
        </div>

      </div> <!-- fim do container -->
    </div><!-- fim do background que tem para deixar o menu com a tela toda -->

    

  </div> <!-- fim do container-flex -->
</template>


<script>
// import AuthenticationService from "@/services/AuthenticationService"
import anuncio from "~/components/anuncios/anuncio"
import moment from 'moment'
import { library } from '@fortawesome/fontawesome-svg-core'
import { faFacebook, faInstagram } from '@fortawesome/free-brands-svg-icons'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

library.add(faFacebook)
library.add(faInstagram)

export default {
    data(){
      return{
        show: false,
        type: "#fff",
        noticia:null,
        itemPesquisado:null,
        horaAtual:null,
      }
      
    },
    components:{
      anuncio,
      FontAwesomeIcon
    },
    
    methods: {
      horaAtualFuncao(){
        
      },
      
      date: function () {
        moment.locale("pt-br");
        return moment().format('LL'); 
      },
      
      navigateTo (){
        
        
        // window.location.reload()
      },
      navigateTu (){
        // this.$router.push({ name: 'root'})
        
      },
      logout(){
        // this.$store.dispatch("setToken", null)
        // this.$store.dispatch("setUser", null)
        // this.$router.push({ name: 'noticiasLista', params: { nome: recebido  } })
      },
      pesquisa(){
        // this.$router.push({ name: 'resultado', params: { nome: this.itemPesquisado  } })
        // window.location.reload()
      },
      noticias(noticiaRecebida){
        // console.log(noticiaRecebida)
        // this.noticia = noticiaRecebida
        // this.$store.dispatch("setNoticia", this.noticia)
      }
    },
    mounted(){
      
    },
    filters: {
      moment: function () {
        moment.locale("pt-br");
        return moment().format('LL'); 
      }
    }
  }
</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

  .pesquisa{
    margin-top:10px;
    display:flex;
    
    
  }
  .btn-pesquisa{
    background-color:#009999;
    border-color:#009999;
    margin-left:10px;
    
  }

  .back{
    background-color:#142248;
    
    position: sticky;
    margin-top:10px; /* altura que está do topo */
    top: 10px; /* altura que vai parar antes do topo */
    
  }
  
  /*acima do cabeçalho*/
  .acima{
    width:100%;
    
  }
  
  .data{
    text-align: left;
    margin-left:25px;
    float:left;
    margin-top:0px;
    font-size:16px;
  }
  .sociais{
    margin-left: 85%;
    margin-top:50px;
  }
  .abaixo{
    width:100%;
    
    
    display:flex;
    /* justify-content: space-between; */
  }
  /*cabeçalho celular*/
    .cabecalho{
      
      width:100%;
      
      margin-top:-40px;
      margin-bottom:-20px;
      
    }
    .logo{
      width:85%;
      margin-left:-40px;
      /* background:red; */
    }

    .logo:hover{
      cursor:pointer;
    }
    

    /*menu */
    .noticias-btn{
      display: none;
    }
    
  /*barra menu*/
  .pc{
    display:none;
  }
  .cel{
    display:block
  }
  .barra{
    
    
    color:white;
    text-transform: uppercase;
    background-color:#142248;
  }
  .cel {
    list-style: none;
    text-align: center;
    margin-top:5px;
  }
  .cel li a{
    color:white;
  }
   .cel li a:hover{
    color: #009999;
    text-decoration: none;
  }
  .botao{
    margin-left:90%;
  }
  .anuncio{
    margin-top:15%;
    width: 30%;
    height:5vh;
    
    margin-left:-15px;
  }

  /*versão pc*/
  
  @media screen and (min-width: 992px){
    .anuncio{
        width:35%;
        margin-left:70px;
        margin-top:10%;
        height:100vh;
        max-height:100px;
        
      }
    .pesquise{
      display:none;
      
    }
    .pesquisa{
      
      display:flex;
      width:445px;
      float:right;
      margin-top:20px;
      
     
      
    }
    .pesquisa div{
      margin-top:6.5px;
    }
    .logo{
        width:65%;
        margin-left:-70px;
        
        
    }
    

    /*barra menu*/
    .cel{
      display:none;
    }
    .pc{display:block}
    .noticias-btn{
      display: block;
    }
    
    .menu ul {
      padding:0px;
      margin-left:0px;
      margin-bottom:0px;
      list-style:none;
    }
    .menu ul li { 
      
      display: inline; }
    .menu ul li a {
      margin-left:5px;
      display: inline-block;
      cursor:pointer;
      /* visual do link */
      font-size: 65%;
      color: white;
      text-decoration: none;
      
  }
  
  
  
    .menu ul li a:hover {
      color:#009999;
      
  }
  .noticias-btn ul {
    position:absolute; 
    top:28px; 
    left:130px;
    border:1px solid #c0c0c0; 
    background-color: #142248; 
    display:none;
  } 
  	
  .noticias-btn:hover ul, .menu li.over ul{display:block;}
  .noticias-btn ul li{
    
    display:block; 
    width:150px;
  }
  .cel{
    display:none;
  }


  

}

@media screen and (min-width: 1200px){
  .menu ul {
      
      margin-left:20px;
      margin-bottom:0px;
      
    }
    
  .menu ul li a {
      margin-left:8px;
      /* visual do link */
      font-size: 12px;
      
      
  }
  .portos-btn ul {
    position:absolute; 
    top:28px; 
    left:950px;
    border:1px solid #c0c0c0; 
    background-color: #142248; 
    display:none;
  } 
  
}

</style>
