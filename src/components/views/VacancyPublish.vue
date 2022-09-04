<template>
  <div class="container py-4">
    <div class="row">
      <div class="col">
        <h4>Add your Vacancy</h4>
      </div>
    </div>
    <div class="row mt-3">
      <div class="col">
        <label for="title-vacancy" class="form-label">Vacancy Title</label>
        <input type="text" class="form-control" v-model="title">
        <div class="form-text">Eg. Javascript, PHP, Vue.js</div>
      </div>
    </div>
    <div class="row mt-3">
      <div class="col">
        <label for="description-vacancy" class="form-label">Vacancy Description</label>
        <textarea type="text" class="form-control" v-model="description"></textarea>
        <div class="form-text">Describe the job</div>
      </div>
    </div>
    <div class="row mt-3">
      <div class="col">
        <label for="salary-vacancy" class="form-label">Vacancy Salary</label>
        <input type="text" class="form-control" v-model="salary">
        <div class="form-text">Salary </div>
      </div>
      <div class="col">
        <label for="modality-vacancy" class="form-label">Modality</label>
        <select class="form-select" v-model="modality">
          <option value="" disabled>Select Modality</option>
          <option value="1">Home-Office</option>
          <option value="2">Hybrid</option>
        </select>
        <div class="form-text">Modality of the job</div>
      </div>

      <div class="col"> 
        <label for="type-vacancy" class="form-label">Type</label>
        <select  class="form-select" v-model="type">
          <option value="" disabled>Select the Type</option>
          <option value="1">CLT</option>
          <option value="2">PG</option>
        </select>
        <div class="form-text">Type of the job</div>
      </div>
    </div>
    <div class="row mt-5">
      <div class="col">
        <button class="btn btn-primary" @click="saveVacancy()">Add Vacancy</button>
      </div>
    </div>
  
  </div>
</template>
<script>
  export default{
    name:'PublishVacancy',
    data: ()=>({
      title:'',
      description:'',
      salary:'',
      modality:'',
      type:'',
      publish:''
    }),
    methods:{
      resetForm(){
        this.title = '',
        this.description ='',
        this.salary = '',
        this.modality='',
        this.type='',
        this.publish=''
      },
      formvalidate(){
      let validate = true

        if(this.title === '')validate = false
        if(this.description === '')validate = false
        if(this.salary === '')validate = false
        if(this.modality === '')validate = false
        if(this.type === '')validate = false

        return validate
      },
      saveVacancy(){
        let actualDate = new Date(Date.now()).toISOString()
        let vacancy = JSON.parse(localStorage.getItem('vacancy'))
        if(!vacancy) vacancy = []

        vacancy.push({
          title: this.title,
          description: this.description,
          salary: this.salary,
          modality: this.modality,
          type: this.type,
          publish: new Date(actualDate).toLocaleString('es-ES')
        })

        if(this.formvalidate()){
          localStorage.setItem('vacancy', JSON.stringify(vacancy))
          this.emitter.emit('alert', {
            type: 'success',
            title: `Vacancy ${this.title}. 'was published.`,
            description: 'Vacancy published Description '
          })
          this.resetForm()
        }else{
            this.emitter.emit('alert', {
              type: 'error',
              title: 'Vacancy. was not published.',
              description: 'Vacancy published Description error'
          })
        }

      }
    }
  }
</script>

