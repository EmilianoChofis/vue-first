<template>
  <div>
    <b-breadcrumb :items="items" />

    <b-list-group>
      <b-list-group-item>Cras justo odio</b-list-group-item>
      <b-list-group-item>Dapibus ac facilisis in</b-list-group-item>
      <b-list-group-item>Morbi leo risus</b-list-group-item>
      <b-list-group-item>Porta ac consectetur ac</b-list-group-item>
      <b-list-group-item>Vestibulum at eros</b-list-group-item>
    </b-list-group>
  </div>
</template>
  
<script>
export default {
  data() {
    return {
      items: [
        {
          text: "Inicio",
          href: "#/inicio",
        },
        {
          text: "Nosotros",
          href: "#/nosotros",
        },
        // {
        //   text: 'Cliente',
        //   active: true
        // }
      ],
    };
  },
};
</script>

<style>
</style>