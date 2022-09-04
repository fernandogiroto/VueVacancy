<template>
        <div class="h-100 p-5 bg-light border rounded-3">
          <h2>Search Vacancy</h2>
          <div class="row">
            <div class="col">
              <div class="form-group">
                <label for="">Vacancy Title</label>
                <input type="text" class="form-control" placeholder="Search for keyworkd" v-model="searchInput">
                <small class="form-text text-muted">Introduce words relateded with the vacancy title that you searching for</small>
              </div>
            </div> 
          </div>
          <div class="row">
            <div class="col">
              <button class="btn btn-outline-dark mt-2" type="button" @click="searchVacancy()">Search</button>
            </div>
          </div>
        </div>
</template>
<script>
    export default {
        name: 'VacancySearch',
        data: ()=>({
          searchInput: ''
        }),
        methods:{
          searchVacancy(){
            this.emitter.emit('searchFilter',{title: this.searchInput})
            console.log('Chegamos ate aqui')
          }
        }
    }
</script>