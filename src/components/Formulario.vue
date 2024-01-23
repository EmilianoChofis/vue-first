<template>
  <div>
    <b-form @submit="checkForm" >
        <p v-if="errors.length">
    <b>Please correct the following error(s):</b>
    <ul>
      <li v-for="error in errors">{{ error }}</li>
    </ul>
  </p>
      <b-form-group id="input-group-2" label="Your Name:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.name"
          placeholder="Enter name"
          
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Your lastname:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.lastname"
          placeholder="Enter lastname"
          
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Your surname:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.surname"
          placeholder="Enter surname"
        ></b-form-input>
      </b-form-group>


      <b-form-group
        id="input-group-2"
        label="Your direccion:"
        label-for="input-2"
      >
        <b-form-input
          id="input-2"
          v-model="form.direccion"
          placeholder="Enter direccion"
          
        ></b-form-input>
      </b-form-group>

      <b-form-group
        id="input-group-2"
        label="Your fecha de nacimiento:"
        label-for="input-2"
      >
        <b-form-input
          id="input-2"
          v-model="form.fec_nac"
          placeholder="Enter Fecha de nacimineto"
          
          type="date"
        ></b-form-input>
      </b-form-group>

      <b-form-group
        id="input-group-2"
        label="Your telefono:"
        label-for="input-2"
      >
        <b-form-input
          id="input-2"
          v-model="form.tel"
          placeholder="Enter Telefono"
        ></b-form-input>
      </b-form-group>

      <b-form-group
        id="input-group-1"
        label="Email address:"
        label-for="input-1"
        description="We'll never share your email with anyone else."
      >
        <b-form-input
          id="input-1"
          v-model="form.email"
          type="email"
          placeholder="Enter email"
          
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
    <b-card class="mt-3" header="Form Data Result">
      <pre class="m-0">{{ form }}</pre>
    </b-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      errors: [],
      form: {
        email: "",
        name: "",
        lastname: "",
        surname: "",
        direccion: "",
        fec_nac: "",
        tel: "",
        foto: "",
      },
    };
  },
  methods: {
    checkForm(e) {
      if (
        this.form.name,
        this.lastname &&
        this.email &&
        this.fec_nac &&
        this.direccion &&
        this.tel
      ) {

        return true;
      }

      this.errors = [];

      if (!this.name) {
        console.log('nombre');
        this.errors.push("El nombre es obligatorio.");
      }
      if (!this.lastname) {
        this.errors.push("El apellido paterno es obligatoria.");
      }

      if (!this.email) {
        this.errors.push('El correo electrónico es obligatorio.');
      } else if (!this.validEmail(this.email)) {
        this.errors.push('El correo electrónico debe ser válido.');
      }

      if (!this.fec_nac) {
        this.errors.push("La fecha de nacimiento es obligatoria.");
      }

      if (!this.direccion) {
        this.errors.push("La dirección es obligatoria.");
      }

      if (!this.tel) {
        this.errors.push("El número de teléfono es obligatorio.");
      }

      //   if (!this.foto) {
      //     this.errors.push("La imagen es obligatoria.");
      //   }
     
      e.preventDefault();
    },
    checkEmail(email) {
      var re =
        /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(email);
    },
  },
};
</script>

<style>
</style>