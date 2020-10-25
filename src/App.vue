<template>
  <v-app>
    <v-app-bar
      app
      color="success"
      dark
    >
      
      <v-spacer></v-spacer>

      <v-btn
        @click="openRegisterModal()"
        target="_blank"
        text
      >
        <span class="mr-2">Cadastrar</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <Busca  @busca="buscarDados"/>
    <v-card>
    <v-card-title>
      Horários da Coleta de reciclados
      <v-spacer></v-spacer>
      <v-text-field
        v-model="search"
        append-icon="mdi-magnify"
        label="Filtro"
        single-line
        hide-details
      ></v-text-field>
    </v-card-title>
    <v-data-table
      :loading="loading"
      :headers="headers"
      :items="horarios"
      :search="search"
    ></v-data-table>
  </v-card>
    </v-main>
  </v-app>
</template>

<script>
import Busca from './components/Busca';

export default {
  name: 'App',

  components: {
    Busca,
  },

  data: () => ({
    cep: null,
    loading: false,
    search: '',
    headers: [
      {
        text: 'CEP',
        align: 'start',
        sortable: false,
        value: 'cep',
      },
      { text: 'Dia da Semana', value: 'dia' },
      { text: 'Endereço', value: 'endereco' },
      { text: 'Horário', value: 'horario' },
    ],
    horarios: [],
  }),
  methods: {
    openRegisterModal(){
      console.log("hello world")
    },
    async buscarDados(value){
      this.loading = true
      this.horarios = []
      await this.$http.get(`http://localhost:5000/horarios?cep=${value}`).then((result)=>{
        if(result && result.status == 200){
          this.horarios = result.data
        }
      })
      this.loading = false
    }
  },
};
</script>
