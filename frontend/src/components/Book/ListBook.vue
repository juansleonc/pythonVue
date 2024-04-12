<template>
    <div class="container">
      <div class="row">
        <div class="col">
          <h2 class="text-left">Listado de libros</h2>
          <div class="my-3">
            <b-button size="sm" variant="primary" :to="{ name: 'NewBook' }">Nuevo libro</b-button>
          </div>
          <b-table striped hover :items="books" :fields="fields" class="col-md-12">
            <template v-slot:cell(action)="data">
              <b-button size="sm" variant="primary" :to="{ name: 'EditBook', params: { bookId: data.item.id } }">Editar</b-button>
              <b-button size="sm" variant="danger" :to="{ name: 'DeleteBook', params: { bookId: data.item.id } }">Eliminar</b-button>
            </template>
          </b-table>
        </div>
      </div>
    </div>
  </template>
  
<script>

import axios from 'redaxios';
export default {
    data() {
        return {
            fields: [
                { key: 'title', label: 'Titulo' },
                { key: 'description', label: 'Description' },
                { key: 'action', label: 'trst', sortable: false },
            ],
            books: [],
            action: []
        }
    },
    methods: {
        getBooks() {
            const path = 'http://127.0.0.1:8000/api/v1.0/books/'
            axios.get(path).then((response) => {
                this.books = response.data
            })
                .catch((error) => {
                    console.log(error)
                })
        }
    },
    created() {
        this.getBooks()
    }
}
</script>

<style lang="css" scoped></style>