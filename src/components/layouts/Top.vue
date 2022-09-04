<template>
  <div>
    <nav class="navbar navbar-expand-lg bg-light">
      <div class="container">
        <a class="navbar-brand" href="#" @click="navigateTo('Home')">Vagas</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0"> 
            <li class="nav-item">
              <a class="nav-link" href="#" @click="navigateTo('PublishVacancy')">Publish Vacancy</a>
            </li>
            <li class="nav-item">
              <a class="btn btn-primary" type="button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasRight" aria-controls="offcanvasRight">Favorites Vacancys</a>
            </li>
          </ul>
        </div>
      </div>
    </nav>
    <div class="offcanvas offcanvas-end" tabindex="-1" id="offcanvasRight" aria-labelledby="offcanvasRightLabel">
        <div class="offcanvas-header">
            <h5 class="offcanvas-title" id="offcanvasRightLabel">Offcanvas right</h5>
            <button type="button" class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close"></button>
        </div>
        <div class="offcanvas-body">
            {{favoriteVacancys}}
        </div>
    </div>
  </div>
</template>
<script>
export default{
  name: "Top",
  data: ()=> ({
    favoriteVacancys : []
  }),
  methods: {
    navigateTo(p){
      this.$emit('navigate',p)
    }
  },
  mounted(){
    this.emitter.on('favoriteVacancy', (title)=>{
      this.favoriteVacancys.push(title)
    })

    this.emitter.on('unFavoriteVacancy', (title)=>{
      let indiceArray = this.favoriteVacancys.indexOf(title);
      if(indiceArray !== -1) this.favoriteVacancys.splice(indiceArray,1)
    })

  }  
}
</script>
<style>
</style>
