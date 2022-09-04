<template>
  <div class="container py-4">
    <div class="row">
      <div class="col">
        <vacancy-search></vacancy-search>
      </div>
    </div>
    <vacancy-list>
      <template v-slot:title="slotProps">{{slotProps.data.title}}</template>
    </vacancy-list>
    <div class="row mt-5">
      <div class="col-4">
        <indicator title="Open Vacancy" indicator="25" bg="bg-dark" color="text-light"></indicator>
      </div>
      <div class="col-4">
        <indicator title="Vue Vacancy" indicator="50" bg="bg-light" color="text-dark"></indicator>
      </div>
      <div class="col-4">
         <indicator title="Closed Vacancy" :indicator="usersOnline" bg="bg-light" color="text-dark"></indicator>
      </div>
    </div>
  </div>
</template>
<script>
  import Indicator from '@/components/utils/Indicator.vue'
  import VacancySearch from '@/components/utils/VacancySearch.vue'
  import VacancyList from '@/components/utils/VacancyList.vue'
    export default{
        name:'Home',
        components:{
          VacancySearch,
          Indicator,
          VacancyList
        },
        data: ()=>({
          usersOnline: 0,
        }),
        methods:{
          randomUsersOnline(){
            this.usersOnline = Math.floor(Math.random() * 101)
          }
        },
      }
</script>

<style></style>
