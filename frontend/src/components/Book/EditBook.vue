<template>
    <div class="container">
        <div class="row">
            <div class="col text-left">
                <h2>Editar libro</h2>
            </div>
        </div>

        <div class="row">
            <div class="col">
                <div class="card">
                    <div class="card-body">
                        <form @submit.prevent="onSubmit">
                            <div class="form-group row">
                                <label for="title" class="col-sm-2 col-form-label">Titulo</label>
                                <div class="col-sm-6">
                                    <input type="text" placeholder="Titulo" name="title" class="form-control"
                                        v-model.trim="form.title">
                                </div>
                            </div>
                            <div class="form-group row">
                                <label for="description" class="col-sm-2 col-form-label">Descripcion</label>
                                <div class="col-sm-6">
                                    <textarea name="description" placeholder="Descripcion" id="" cols="30" rows="10"
                                        class="form-control" v-model.trim="form.description"></textarea>
                                </div>
                            </div>
                            <div class="row">
                                <div class="col text-left">
                                    <b-button type="submit" variant="primary">Editar</b-button>
                                    <b-link :to="{ name: 'ListBook' }">
                                        <b-button variant="secondary">Cancelar</b-button>
                                    </b-link>
                                </div>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'redaxios';
import swal from 'sweetalert';

export default {
    data() {
        return {
            bookId: this.$route.params.bookId,
            form: {
                title: '',
                description: '',
            },
        }
    },
    methods: {
        onSubmit(evt) {
            evt.preventDefault()
            const path = `http://127.0.0.1:8000/api/v1.0/books/${this.bookId}/`
            axios.put(path, this.form).then((response) => {
                this.form.title = response.data.title
                this.form.description = response.data.description

                swal('Libro actualizado exitosamente!!', '', 'success')
            }).catch((error) => {
                console.log(error)
            })
        },
        getBook() {
            const path = `http://127.0.0.1:8000/api/v1.0/books/${this.bookId}/`
            console.log(path)

            axios.get(path).then((response) => {
                console.log(response.data)
                this.form.title = response.data.title
                this.form.description = response.data.description
            }).catch((error) => {
                console.log(error)
            })
        }
    },
    created() {
        this.getBook()
    }

}
</script>