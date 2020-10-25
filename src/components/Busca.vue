<template>
  <v-container>
    <v-toolbar flat color="white">
              <v-toolbar-title>Buscar por CEP</v-toolbar-title>
              <v-divider class="mx-4" inset vertical></v-divider>
                <v-text-field type="number" txt v-model="search" solo prepend-inner-icon="mdi-search" ></v-text-field>
              <v-divider class="mx-4" inset vertical></v-divider>
                <v-dialog v-model="dialog" max-width="500px">
                <template v-slot:activator="{ on }">
                  <v-btn color="success" dark class="mb-2" v-on="on" @click="buscarDados()" >Buscar</v-btn>
                </template>
              </v-dialog>
            </v-toolbar>
  </v-container>
</template>

<script>
  export default {
    name: 'HelloWorld',

    data: () => ({
      dialog: true,
      search: ""
    }),
    methods:{
      buscarDados(){
           this.$emit("busca", this.search);
      }
    }
  }
</script>

<style  scoped>
  .v-text-field.v-text-field--enclosed{
    margin-top: 20px;
  }
</style>
