# PJ_ZDZ
Teste avaliação

**ESCOPO** 
O projeto ira cadastrar produtos sendo ele com categorias quantidades e valores, sendo possivel a exclusão dos dados e visualização do mesmo. 

Diagrama:

![image](https://github.com/PeeHR/PJ_SAPATEK/assets/128930886/58deb8a7-abca-4280-9038-419ab98cd2b1)

pagina inicial:

![image](https://github.com/PeeHR/PJ_SAPATEK/assets/128930886/716ca4ce-2961-4895-83dd-4d936506e6f6)

Area de cadastro de produtos:
![image](https://github.com/PeeHR/PJ_SAPATEK/assets/128930886/5810c109-8758-48a4-b217-42f1e1b19838)

**Codigo fonte:(cadastro produtos)**
API ENVIADA.

<template>
    <v-form ref="form" prevent.submit>

        <v-toolbar density="compact" :elevation="8"> Cadastro de produtos </v-toolbar>
        <v-container>

            <v-row>
                <v-col cols="12" md="4"><v-text-field v-model="produtos.nome" :rules="nameRules" :counter="2"
                        label="Nome do produto" hide-details required></v-text-field> </v-col>
                <v-col cols="12" md="4"><v-text-field v-model="produtos.quantidade" :rules="nameRules" :counter="2"
                        label="Quantidade" hide-details required></v-text-field></v-col>
                <v-col cols="12" md="4"><v-text-field v-model="produtos.preco" :rules="nameRules" :counter="2"
                        label="Preço" hide-details required></v-text-field></v-col>
                <v-col cols="12" md="4"><v-text-field v-model="produtos.descricao" :rules="nameRules" :counter="2"
                        label="Descrição do produto" hide-details required></v-text-field></v-col>
                <v-col cols="12" md="4"><v-text-field v-model="produtos.categoria_nome" label="Informe a categoria"
                        hide-details required></v-text-field></v-col>
                <v-col cols="12" md="4"><v-text-field v-model="produtos.tipo" label="Tipo do produto" hide-details
                        required></v-text-field></v-col>
            </v-row>
            <v-container></v-container>

            <v-btn class="mt-4" @click="teste()">cadastrar</v-btn>
            <v-btn class="mt-4" @click="clear()">Limpar</v-btn>

        </v-container>
        
    </v-form>
</template>

<script>
import axios from "axios";

export default {
    data: () => ({

        produtos: {

            nome: '',
            quantidade: '',
            preco: '',
            descricao: '',
            categoria: '',
            tipo: '',

        },

        valid: false,
        nome: '',
        quantidade: '',
        preco: '',
        descricao: '',
        categoria: '',
        tipo: '',
        nameRules: [
            value => {
                if (value) return true

                return 'Name is required.'
            },
        ],

        teste: async function () {
        
            

            let bodyContent = this.produtos

            let reqOptions = {
                url: "https://localhost:7001/ControllerZDZ/produtos",
                method: "POST",
        
                data: bodyContent,
            }

            let response = await axios.request(reqOptions);
            console.log(response.data);
            
            this.$refs.form.reset()
      
        },

        clear () {
        this.$refs.form.reset()
      },
  

    })


}

</script>
<style></style>

**Codigo fonte tela inicial**
<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card class="logo py-4 d-flex justify-center">
       <img src="foto.jpeg" alt="center">
      </v-card>
      <v-card>
        <v-card-title class="headline">
          Seja Bem vindo ao meu texte ZDZ!
        </v-card-title>
        <v-card-text>
          <p>Meu nome e Pedro Vinicius</p>
          <p> Para acessar meu GitHub Clique aqui: <a
              href="https://github.com/PeeHR"
              target="_blank"
              rel="noopener noreferrer"
            >GitHub
              
            </a>. 
          </p>
          <p>
            Meu numero de contato esta abaixo tambem! <a
              href="https://wa.me/5531994548735?text=Ol%C3%A1+voc%C3%AA+est%C3%A1+sendo+direcionado+para+o+Pedro%21"
              target="_blank"
              rel="noopener noreferrer"
              title="chat"
            >
              WhatsApp
            </a>.
          </p>
          
          <p>Desde já agradeço a atenção!</p>
          <div class="text-xs-right">
            <em><small>&mdash; Pedro Vinicius da Silva Costa (Junior Develop)</small></em>
          </div>
          
        </v-card-text>
        <v-card-actions>
          <v-spacer />
          <v-btn
            color="primary"
            nuxt
            to="/produtos"
          >
            Continue
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'IndexPage'
}

</script>


