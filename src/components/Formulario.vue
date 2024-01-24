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
      <b-form-group id="surname" label="Your surname:" label-for="surname">
        <b-form-input
            id="surname"
            v-model="form.surname"
            placeholder="Enter surname"
        ></b-form-input>
      </b-form-group>

      <b-form-row>
        <b-form-group
            id="cp"
            label="Your CP:"
            label-for="cp"
        >
          <b-form-input
              id="cp"
              v-model="form.direccion.cp"
              placeholder="Enter cp"

          ></b-form-input>
          <b-form-group
              id="calle"
              label="Your Street:"
              label-for="calle"
          >
            <b-form-input
                id="calle"
                v-model="form.direccion.calle"
                placeholder="Enter street"
            ></b-form-input>
          </b-form-group>

          <!-- Componente para el número exterior -->
          <b-form-group
              id="num_ext"
              label="Your Exterior Number:"
              label-for="num_ext"
          >
            <b-form-input
                id="num_ext"
                v-model="form.direccion.num_ext"
                placeholder="Enter exterior number"
            ></b-form-input>
          </b-form-group>

          <!-- Componente para la ciudad -->
          <b-form-group
              id="ciudad"
              label="Your City:"
              label-for="ciudad"
          >
            <b-form-input
                id="ciudad"
                v-model="form.direccion.ciudad"
                placeholder="Enter city"
            ></b-form-input>
          </b-form-group>
        </b-form-group>

      </b-form-row>

      <b-form-group
          id="fec_nac"
          label="Your fecha de nacimiento:"
          label-for="fec_nac"
      >
        <b-form-input
            id="fec_nac"
            v-model="form.fec_nac"
            placeholder="Enter Fecha de nacimineto"

            type="date"
        ></b-form-input>
      </b-form-group>

      <b-form-group
          id="tel"
          label="Your telefono:"
          label-for="tel"
      >
        <b-form-input
            id="tel"
            v-model="form.tel"
            placeholder="Enter Telefono"
        ></b-form-input>
      </b-form-group>

      <b-form-group
          id="email"
          label="Email address:"
          label-for="email"
          description="We'll never share your email with anyone else."
      >
        <b-form-input
            id="email"
            v-model="form.email"
            type="email"
            placeholder="Enter email"

        ></b-form-input>
      </b-form-group>
      <b-form-group
          id="foto"
          label="Your foto:"
          label-for="foto"
      >
        <b-form-input
            id="foto"
            v-model="form.foto"
            placeholder="Enter foto"
            type="file"
            accept="image/*"
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
        direccion:{
          cp: "",
          calle:"",
          num_ext: "",
          ciudad: ""
        },
        fec_nac: "",
        tel: "",
        foto: "",
      },
    };
  },
  methods: {
    checkForm(e) {
      this.errors = [];
      if (
          this.form.name &&
          this.form.lastname &&
          this.form.email &&
          this.form.fec_nac &&
          this.form.direccion.cp &&
          this.form.direccion.calle &&
          this.form.direccion.num_ext &&
          this.form.direccion.ciudad &&
          this.form.tel
      ) {
        console.log('logra');

        return true;
      }



      if (!this.form.name) {
        this.errors.push("El nombre es obligatorio.");
      } else if (this.checkIsString(this.form.name)) {
        this.errors.push("El nombre debe ser válido.");}

       if (!this.form.lastname) {
         this.errors.push("El apellido paterno es obligatoria.");
       } else if (this.checkIsString(this.form.lastname)) {
         this.errors.push("El apellido paterno debe ser válido.");
       }

       if(!this.form.direccion.cp){
         this.errors.push("El código postal es obligatorio.");
       } else if(this.form.direccion.cp.length != 5){
         this.errors.push("El código postal debe tener 5 dígitos.");
       }

        if(!this.form.direccion.calle){
          this.errors.push("La calle es obligatoria.");
        }

        if(!this.form.direccion.num_ext){
          this.errors.push("El número exterior es obligatorio.");
        }

        if(!this.form.direccion.ciudad){
          this.errors.push("La ciudad es obligatoria.");
        }


        if(!this.form.fec_nac){
          this.errors.push("La fecha de nacimiento es obligatoria.");
        }

        if(this.form.fec_nac){
          var fecha_actual = new Date();
          var fecha_nac = new Date(this.form.fec_nac);
          var edad = fecha_actual.getFullYear() - fecha_nac.getFullYear();
          if(edad > 18){
            this.errors.push("Lo sentimos, limite de 18 años.");
          }
        }

        if (!this.form.tel) {
          this.errors.push("El número de teléfono es obligatorio.");
        } else if (this.form.tel.length != 10) {
          this.errors.push("El número de teléfono debe tener 10 dígitos.");
        }

        if (!this.form.email) {
          this.errors.push("El correo electrónico es obligatorio.");
        } else if (!this.checkEmail(this.form.email)) {
          this.errors.push("El correo electrónico debe ser válido.");
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
    checkIsString(value) {
      return typeof value === "string" || value instanceof String;
    },
  },
};
</script>

<style>
</style>