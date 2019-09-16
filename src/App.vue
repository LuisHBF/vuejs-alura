<template>
  <div>
    <h3>{{ titulo }}</h3>
    <ul>
      <li li v-for="foto of fotos">
        <img :src="foto.url" :alt="foto.titulo">
      </li>
    </ul>
  </div>
</template>

<script>
export default {

  data() {

    return {
      'titulo' : 'PIC',
      'fotos' : [
        {
        url : 'https://encrypted-tbn2.gstatic.com/images?q=tbn:ANd9GcTwV4kVzT5McBdGSgqlVeRzubrNH_mOrrkKseDOGFURq20HmsrelEfMU7It',
        titulo: 'Cachorro'
        },
        {
        url : 'https://encrypted-tbn2.gstatic.com/images?q=tbn:ANd9GcTwV4kVzT5McBdGSgqlVeRzubrNH_mOrrkKseDOGFURq20HmsrelEfMU7It',
        titulo: 'Cachorrão'
        }
      ]


    }
  },

  created(){
    this.$http.get('http://localhost:3000/v1/fotos')
    .then(res => res.json())
    .then(fotos => this.fotos = fotos, err => console.log(err));
  }
}
</script>

<style>

</style>
