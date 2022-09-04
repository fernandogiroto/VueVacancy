<template>
        <div class="card">
          <div class="card-header bg-dark text-white">
            <div class="row">
              <div class="col d-flex justify-content-between">
                <div>{{title}}</div>
                <div>
                  <div class="form-check form-switch">
                    <input class="form-check-input" type="checkbox" v-model="favorite"> 
                    <label class="form-check-label" >Favorite </label>
                  </div>
                  </div>
              </div>
            </div>
            
            </div>
          <div class="card-body">{{description}}</div>
          <div class="card-footer">
            <small class="text-muted">Salary: {{salary}} | Modality: {{getModality}} | Type: {{getType}} | Publish: {{publish}}</small>
          </div>
        </div>
</template>

<script>

export default {
    name:'Vacancy',
    data: ()=> ({
      favorite: false
    }),
    watch:{
      favorite(newValue){
        if(newValue){
          this.emitter.emit('favoriteVacancy', this.title)
        }
        else{
          this.emitter.emit('unFavoriteVacancy', this.title)
        }
      }
    },
    methods:{
 
    },
    props: {
        title: {type:String,required:true,validator(p){if(p.length > 5)return true}},
        description: {type:String,default:'Descrição não enviada'},
        salary: {type:[Number,String],required:true},
        modality:{type:String,required:true},
        type: {type:String,required:true},
        publish: {type:String,required:true},
    },
    computed:{
      getType(){
        switch(this.type){
          case '1' : return 'CLT'
          case '2' : return 'PJ'
        }
      },
      getModality(){
        switch(this.modality){
          case '1' : return 'Home-Office'
          case '2' : return 'Hybrid'
        }
      }
    }
}
</script>
