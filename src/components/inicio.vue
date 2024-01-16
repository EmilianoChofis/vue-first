

<template>
  <div>
    <b-breadcrumb :items="items"/>
    <clientes/>
    <b-card
      title="Card Title"
      img-src="https://picsum.photos/600/300/?image=25"
      img-alt="Image"
      img-top
      tag="article"
      style="max-width: 20rem"
      class="mb-2"
    >
      <b-card-text>
        Some quick example text to build on the card title and make up the bulk
        of the card's content.
      </b-card-text>

      <b-button href="#" variant="primary">Go somewhere</b-button>
    </b-card>
    
   
  </div>
</template>


<script>
export default {
  data() {
    return {
      items: [
        {
          text: 'Inicio',
          href: '#/inicio'
        },
        // {
        //   text: 'Nosotros',
        //   href: '#/nosotros'
        // },
        // {
        //   text: 'Cliente',
        //   active: true
        // }
      ]
    }
  }
}
</script>

<style>
</style>