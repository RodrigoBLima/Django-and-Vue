<template lang="html">

    <div class="container">

          <div class="row">
              <div class="col text-left">
                  <h2>Editar livros</h2>
               </div>
          </div>

            <div class="row">
              <div class="col">
                 <div class="card">
                    <div class="card-body">

                      <form @onSubmit="onSubmit">

                        <div class="form-group row">
                            <label for="title" class="col-sm-2 col-form-label">Titulo</label>
                            <div class="col-sm-6">
                              <input type="text" placeholder="Digite o titulo do livro" name="title" class="form-control" v-model.trim="form.title">
                            </div>
                        </div>
                        <div class="form-group row">
                            <label for="description" class="col-sm-2 col-form-label">Descrição</label>
                            <div class="col-sm-6">
                              <textarea type="text" rows="3" placeholder="Digite a descrição do livro" name="description" class="form-control" v-model.trim="form.description"></textarea>
                            </div>
                        </div>
                          <div class="rows">
                              <div class="col text-left">
                                  <b-button type="submit" variant="primary"> Editar </b-button>
                                  <b-button type="submit" class="btn-large-space" :to="{name: 'ListBook'}" > Cancelar </b-button>
                              </div>
                          </div>
                      </form>

                    </div>
                  </div>
                </div>
              <div>
          </div>
        </div>
    </div>

</template>

<script>
import axios from 'axios';

  export default{
   data() {
      return {
        bookId: this.$route.params.bookId,
        form: {
          title: '',
          description: ''
        }
      }
    },
    methods:{

      onSubmit(evt){

        evt.preventDefault()

      },

      getBook(){

        const path = `http://127.0.0.1:8000/api/v1.0/books/${this.bookId}`

        axios.get(path).then((response) => {

          this.form.title = reponse.data.title
          this.form.description = response.data.description

        })
        .catch((error) => {
          conole.log(error)
        })
      }

    },
    created() {
      this.getBook()
    },

  }
</script>

<style lang="css" scoped>

</style>
