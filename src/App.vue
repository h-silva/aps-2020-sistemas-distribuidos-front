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
      :headers="headers"
      :items="desserts"
      :search="search"
    ></v-data-table>
  </v-card>
    </v-main>
  </v-app>
</template>

<script>
import Busca from './components/Busca';

export default {
  cep: 'App',

  components: {
    Busca,
  },

  data: () => ({
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
        desserts: [
          {
            cep: '16250000',
            dia: "Segunda-Feira",
            endereco: "Luzia Figueiredo Rizzato",
            horario: "10:00",
          },
          {
            cep: '16250000',
            dia: "Terça-Feira",
            endereco: "Luzia Figueiredo Rizzato",
            horario: "10:00",
          },
          {
            cep: '16250000',
            dia: "Quarta-Feira",
            endereco: "Luzia Figueiredo Rizzato",
            horario: "10:00",
          },
          {
            cep: '16250000',
            dia: "Quinta-Feira",
            endereco: "Luzia Figueiredo Rizzato",
            horario: "10:00",
          },
          {
            cep: '16250000',
            dia: "Sexta-Feira",
            endereco: "Luzia Figueiredo Rizzato",
            horario: "10:00",
          },
          {
            cep: '16250000',
            dia: "Sábado",
            endereco: "Luzia Figueiredo Rizzato",
            horario: "10:00",
          },
          {
            cep: '16250000',
            dia: "Domingo",
            endereco: "Luzia Figueiredo Rizzato",
            horario: "10:00",
          },
        ],
  }),
  methods: {
    openRegisterModal(){
      console.log("hello world")
    },
    buscarDados(value){
      alert("buscando cep: " + value)
    }
  }
};
</script>
