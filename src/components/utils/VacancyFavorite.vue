<template>
    <!-- <button class="btn btn-primary" type="button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasRight" aria-controls="offcanvasRight">Favorites Vacancys</button>

    <div class="offcanvas offcanvas-end" tabindex="-1" id="offcanvasRight" aria-labelledby="offcanvasRightLabel">
        <div class="offcanvas-header">
            <h5 class="offcanvas-title" id="offcanvasRightLabel">Offcanvas right</h5>
            <button type="button" class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close"></button>
        </div>
        <div class="offcanvas-body">
            {{favoriteVacancys}}
        </div>
    </div> -->
    <div></div>
</template>
<script>
    export default {
        name: 'VacancyFavorite',
        data: ()=> ({
            favoriteVacancys : []
        }) ,
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