<template>
  <vacancy-favorite></vacancy-favorite> 
  <alert v-if="showAlert" :type="alert.type"> 
    <template v-slot:title>
      <h5>{{alert.title}}</h5>
    </template>
    <template v-slot:description>
      <h5>{{alert.description}}</h5>
    </template>
  </alert>
  <top @navigate="component = $event"></top>
  <content v-if="visible" :content="component"></content>
</template>

<script>
import Content from '@/components/layouts/Content.vue'
import Top from '@/components/layouts/Top.vue'
import VacancyFavorite from '@/components/utils/VacancyFavorite.vue'
import Alert from '@/components/utils/Alert.vue' 

export default {
  name: 'App',
  data:()=>({ 
    visible: true,
    component : 'home',
    showAlert: false,
    alert: { title:'', description:'', type:''}
  }),
  components: {
    Alert,
    Content,
    Top,
    VacancyFavorite
  },
  mounted(){
    this.emitter.on('alert',(AlertParameters)=> {
      this.alert = AlertParameters;
      this.showAlert = true;
      setTimeout(()=> this.showAlert=false,4000)
    })
  }
}
</script> 
