<template>
  <div>
    <keep-alive>
      <component :is="content" />
    </keep-alive>
  </div>
</template>

<script>
import Home from '@/components/views/Home.vue';
import PublishVacancy from '@/components/views/VacancyPublish.vue';

export default{
  name:'Content',
  props:{
    content:{
      require: true,
      type: String 
    }
  }, 
  components:{
    Home,
    PublishVacancy
  },
  data: ()=>({
  }),
  // beforeUnmount(){
  //   console.log('Before Unmounted')
  // },
  // unmounted(){
  //   console.log('Unmonted')
  // },

  // beforeCreate() {
  //   console.log('Antes de criar', this.teste)
  // },
  // created() {
  //   console.log('Criado', this.teste)
  // },
  // beforeMount() {
  //   console.log('Antes de montar o template')
  // },
  // mounted() {
  //   console.log('Montado')
  // },
  // beforeUpdate() {
  //   console.log('Antes de atualizar')
  // },
  // updated() {
  //   console.log('Atualizado')
  // },
  // beforeUnmount() {
  //   console.log('Antes de demonstar/destruir')
  // },
  // unmounted() {
  //   console.log('Demonstado/destruído')
  // },
  // errorCaptured() {
  //   console.log('Erro capturado')
  // },
  // renderTracked() {
  //   console.log('Re-renderização rastreada')
  // },
  // renderTriggered() {
  //   console.log('Re-renderização acionada')
  // },
  // activated() {
  //   console.log('Componente é ativado')
  // },
  // deactivated() {
  //   console.log('Componente é desativado')
  // }
  
}
</script>
