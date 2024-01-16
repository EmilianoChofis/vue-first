<template>
  <div class="text-center">
    <b-breadcrumb :items="items" />
    <b-spinner label="Spinning"></b-spinner>
    <b-spinner type="grow" label="Spinning"></b-spinner>
    <b-spinner variant="primary" label="Spinning"></b-spinner>
    <b-spinner variant="primary" type="grow" label="Spinning"></b-spinner>
    <b-spinner variant="success" label="Spinning"></b-spinner>
    <b-spinner variant="success" type="grow" label="Spinning"></b-spinner>
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
        {
          text: "Cliente",
          active: true,
        },
      ],
    };
  },
};
</script>

<style>
</style>