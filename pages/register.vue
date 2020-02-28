<template>
  <section class="container" >

    
   
      <h1 class="title">
        {{msg.error}}
      </h1>
    
    <v-form                 
    ref="form"
    lazy-validation
    >

      <v-text-field
      v-model="barcodeValue"
      label="Barcode"
      required 
    ></v-text-field>


    <br>
  <barcode v-bind:value="barcodeValue">
    Show this if the rendering fails.
  </barcode>
    <v-text-field
      v-model="form.name"
      label="Name"
      required 
    ></v-text-field>

    <v-text-field
      v-model="form.email"
      label="E-mail"
      required
    ></v-text-field>

    <v-text-field
      v-model="form.password"
      type="password"
      label="Password"
      required
    ></v-text-field>

    <v-text-field
      v-model="form.confirm_password"
      type="password"
      label="Confirm Password"
      required
    ></v-text-field>

    <v-btn
      color="success"
      class="mr-4"
      @click="register"
    >
      Submit
    </v-btn>

  </v-form>
  <!-- <a />
  <b />
  <c /> -->
   </section>
</template>

<script>
import VueBarcode from 'vue-barcode';
//import { QrcodeStream, QrcodeDropZone, QrcodeCapture } from 'vue-qrcode-reader'

export default {

  components: {
    'barcode': VueBarcode,
    //  'a':QrcodeStream,
    // 'b':QrcodeDropZone,
    // 'c':QrcodeCapture
  },

auth:false,
layout:'login',
data:() => ({
  barcodeValue:'',
      form: {
            name : "",
            email : "",
            password :"",
            confirm_password : ""

          },
          msg:""
}),
methods:{
  register(){
      this.$axios.post('register',this.form)
      .then((res) => {
        console.log(res.data);
      });
  
  },
  
}

}
</script>