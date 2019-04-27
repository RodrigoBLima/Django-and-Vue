<template lang="html">

    <div class="container">
        <div class="row">
          <div class="col">
              <h3>Realmente deseja excluir esse livro?</h3>


                 <div class="card">
                    <div class="card-body">

                            <p>Titulo : {{ this.element.title }}</p>
                            <p>Descrição : {{ this.element.description }}</p>

                            <div class="row">
                              <div class="col">
                                <b-button v-on:click="deleteBook" variant="danger"> Deletar </b-button>
                                <b-button type="submit" class="btn-large-space" :to="{name: 'ListBook'}" > Cancelar </b-button>
                              </div>
                            </div>
                      </div>
                  </div>
            </div>
          </div>
       </div>

</template>
<script>
import axios from 'axios';
import swal from "sweetalert";

export default {
    data() {
      return {
        bookId: this.$route.params.bookId,
        element: {
          title: '',
          description: ''
        }
      }
    },
    methods: {
      getBook(){

        const path = `http://127.0.0.1:8000/api/v1.0/books/${this.bookId}/`

        axios.get(path).then((response) => {

          this.element.title = response.data.title
          this.element.description = response.data.description

        })
        .catch((error) => {
          console.log(error)
        })
      },
      deleteBook(){
         const path = `http://127.0.0.1:8000/api/v1.0/books/${this.bookId}/`

          axios.delete(path).then((response) => {
            location.href = '/books'
          })
          .catch((error) => {
               swal("Não foi possível excluir este livro", "", "error")
          })
      }
    },
    created() {
      this.getBook()
    },


}
</script>
<style lang="">

</style>
