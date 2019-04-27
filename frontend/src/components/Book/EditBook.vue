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
                              <input type="text" placeholder="Digite o titulo do livro" name="title" class="form-control">
                            </div>
                        </div>
                        <div class="form-group row">
                            <label for="description" class="col-sm-2 col-form-label">Descrição</label>
                            <div class="col-sm-6">
                              <textarea type="text" rows="3" placeholder="Digite a descrição do livro" name="description" class="form-control"></textarea>
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

</script>

<style lang="css" scoped>

</style>
