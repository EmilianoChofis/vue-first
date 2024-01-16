<template>
    <b-breadcrumb :items="items"></b-breadcrumb>
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
            {
              text: 'Nosotros',
              href: '#/nosotros'
            },
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