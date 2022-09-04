<template>
    <slot name ="title" :data="{title:''}">
        <h1>Avaiable Vacancys</h1>
    </slot>
    <slot :vacancys="vacancys">
    <div class="row mt-5" v-for="(vacancy, index) in vacancys" :key="index">
      <div class="col">
        <vacancy v-bind="vacancy"/>
      </div>  
    </div>
    </slot>
</template>
<script>
    import Vacancy from '@/components/utils/Vacancy.vue'
    export default {
        name: 'VacancyList',
        data: ()=> ({
            vacancys: []
        }),
        components:{
            Vacancy
        },
        activated() {     
          this.vacancys = JSON.parse(localStorage.getItem('vacancy'));
        },
        mounted(){
          this.emitter.on('searchFilter',vacancyFilter => {
          const vacancy = JSON.parse(localStorage.getItem('vacancy'));
          this.vacancys = vacancy.filter(register => register.title.toLowerCase().includes(vacancyFilter.title.toLowerCase())) 
          })
        }
    }
</script>