<template>
<div class="Desktop1 w-full flex-col justify-start items-start inline-flex">
  <div class="whatsapp">
    <a href="https://wa.me/+554184290372">
      <img src="WhatsApp.png" alt="" style="width: 64px;">
    </a>
  </div>

  <div class="Navbar self-stretch px-4 md:px-24 py-4 bg-veb justify-between items-center gap-5 inline-flex">
    <div class="VenezolanosEnBrazil text-sky-900 text-2xl font-bold">VENEZOLANOS EN BRAZIL</div>
    <div class="Frame3  self-stretch px-5 justify-end items-center gap-5 flex" v-if="false">
      <a v-for="link in navbar" :key="link.url" class="text-black text-base font-normal" :href="link.url" > {{ link.name }} </a>
    </div>
  </div>
  <div class="Hero self-stretch px-4 md:px-24 bg-veb grid grid-cols-1 md:grid-cols-2 gap-5">
    <div class="flex flex-col justify-center gap-10">
      <div class="flex text-sky-900 text-4xl font-bold justify-center text-center">
        REALIZA CAMBIOS DE<br/>BOLÍVARES  Y REALES
      </div>
      <div class="flex flex-col items-center rounded-lg gap-5">
        <div class="bg-white p-5 flex-col justify-center content-center items-center rounded-lg gap-5 flex">
          <div class="Row justify-start items-start gap-5 lg:inline-flex">
            <div class="Input flex-col justify-start items-start gap-3 inline-flex">
              <label for="first_name" class="text-gray-700">Nombres</label>
              <input v-model="formData.first_name" type="text" id="first_name" name="first_name" class="border-solid border border-gray-300 rounded-md focus:ring focus:ring-opacity-50">
            </div>
            <div class="Input flex-col justify-start items-start gap-3 inline-flex">
              <label for="last_name" class="text-gray-700">Apellidos</label>
              <input v-model="formData.last_name" type="text" id="last_name" name="last_name" class="border-solid border border-gray-300 rounded-md focus:ring focus:ring-opacity-50">
            </div>
          </div>
          <div class="Row justify-start items-start gap-5 lg:inline-flex">
            <div class="Input flex-col justify-start items-start gap-3 inline-flex">
              <label for="email" class="text-gray-700">Email</label>
              <input v-model="formData.email" type="email" id="email" name="email" class="border-solid border border-gray-300 rounded-md focus:ring focus:ring-opacity-50">
            </div>
            <div class="Input flex-col justify-start items-start gap-3 inline-flex">
              <label for="phone" class="text-gray-700">Telefono</label>
              <input v-model="formData.phone" type="text" id="phone" name="phone" class="border-solid border border-gray-300 rounded-md focus:ring focus:ring-opacity-50">
            </div>
          </div>
          <div class="Row justify-start items-start gap-5 lg:inline-flex">
            <div class="Input flex-col justify-start items-start gap-3 inline-flex">
              <label for="banking" class="text-gray-700">Banco</label>
              <input v-model="formData.banking" type="text" id="banking" name="banking" class="border-solid border border-gray-300 rounded-md focus:ring focus:ring-opacity-50">
            </div>
            <div class="Input flex-col justify-start items-start gap-3 inline-flex">
              <label for="id_number" class="text-gray-700">Cedula de Identidad</label>
              <input v-model="formData.id_number" type="text" id="id_number" name="id_number" class="border-solid border border-gray-300 rounded-md focus:ring focus:ring-opacity-50" maxlength="10">
            </div>
          </div>
          <div class="Row justify-start items-start gap-5 lg:inline-flex">
            <div class="Input flex-col justify-start items-start gap-3 inline-flex">
              <label for="account_number" class="text-gray-700">Numero de Cuenta</label>        
              <input v-model="formData.account_number" type="text" id="account_number" name="account_number" class="border-solid border border-gray-300 rounded-md focus:ring focus:ring-opacity-50" maxlength="20">
            </div>
          </div>
          <div class="bg-green-500 p-4 text-white" v-if="success">
            <p>
              {{ success }}
            </p>
            <a href="https://wa.me/+554184290372" style="text-decoration: underline; font-weight: bold;">
              Contactanos por Whatsapp a este numero
            </a>
          </div>
          <div class="bg-red-500 p-4 text-white" v-if="error">
            {{ error }}
          </div>
          <div class="Button flex-col justify-center items-center gap-5 flex">
            <div class="Button px-5 rounded flex-col justify-center items-center flex">
              <button @click="submitForm()" :disabled="activeRequest" class="w-full bg-green-500 text-white py-2 px-4 rounded-md hover:bg-green-600 flex-row justify-center items-center flex align-center">
                <span class="mx-4">Contactanos</span>
                <span v-show="activeRequest">
                  <svg aria-hidden="true" class="w-8 h-8 mr-2 text-gray-200 animate-spin dark:text-gray-600 fill-blue-600" viewBox="0 0 100 101" fill="none" xmlns="http://www.w3.org/2000/svg">
                      <path d="M100 50.5908C100 78.2051 77.6142 100.591 50 100.591C22.3858 100.591 0 78.2051 0 50.5908C0 22.9766 22.3858 0.59082 50 0.59082C77.6142 0.59082 100 22.9766 100 50.5908ZM9.08144 50.5908C9.08144 73.1895 27.4013 91.5094 50 91.5094C72.5987 91.5094 90.9186 73.1895 90.9186 50.5908C90.9186 27.9921 72.5987 9.67226 50 9.67226C27.4013 9.67226 9.08144 27.9921 9.08144 50.5908Z" fill="currentColor"/>
                      <path d="M93.9676 39.0409C96.393 38.4038 97.8624 35.9116 97.0079 33.5539C95.2932 28.8227 92.871 24.3692 89.8167 20.348C85.8452 15.1192 80.8826 10.7238 75.2124 7.41289C69.5422 4.10194 63.2754 1.94025 56.7698 1.05124C51.7666 0.367541 46.6976 0.446843 41.7345 1.27873C39.2613 1.69328 37.813 4.19778 38.4501 6.62326C39.0873 9.04874 41.5694 10.4717 44.0505 10.1071C47.8511 9.54855 51.7191 9.52689 55.5402 10.0491C60.8642 10.7766 65.9928 12.5457 70.6331 15.2552C75.2735 17.9648 79.3347 21.5619 82.5849 25.841C84.9175 28.9121 86.7997 32.2913 88.1811 35.8758C89.083 38.2158 91.5421 39.6781 93.9676 39.0409Z" fill="white"/>
                  </svg>
                    <span class="sr-only">Loading...</span>
                </span>
              </button>
            </div>
          </div>
        </div>
        
      </div>
      <!--
      <div class="flex flex-col h-12 p-2 justify-center items-center">
        <div class="Badge bg-white rounded-full border border-white justify-center items-center gap-5 inline-flex">
          <img class="Image6 w-10 h-10 rounded-full" src="vzla.png" />
          <div class="VesX1Brl text-center text-black text-base font-normal">{{ves}} VES x {{brl}} BRL</div>
          <img class="Image6 w-10 h-10 rounded-full" src="brazil.png" />
        </div>
      </div>
      -->
    </div>
    <div class="flex flex-col justify-center items-center">
      <img class="hero-image" src="venezolanos-en-brazil.png" />
    </div>
  </div>
</div>
</template>

<script>
import axios from "axios"
export default {
  name: 'IndexPage',
  data () {
    return {
      ves: 6,
      brl: 1,
      activeRequest: false,
      navbar: [
        { name: "Tramites", url: "/tramites"},
        { name: "Ofertas de trabajo", url: "/Ofertas-de-trabajo"},
        { name: "Productos Venezolanos", url: "/Productos-venezolanos"},
        { name: "Cambios de Divisas", url: "/Cambios-de-Divisas"},
        { name: "Boletos Aereos", url: "/Boletos-Aereos"},
      ],
      bancos : [],
      formData: {
        first_name: '',
        last_name: '',
        email: '',
        phone: '',
        banking: '',
        id_number: '',
        account_number: '',
      },
      error: false,
      success: false,
    }
  },
  created () {
    console.log(
      process.env.WHATSAPP_TOKEN
      )
  },
  methods: {
    resetState () {
      this.activeRequest = this.error = this.success = false
    },
    submitForm() {

      if (
        this.formData.first_name == "" ||
        this.formData.last_name == "" ||
        this.formData.email == "" ||
        this.formData.phone == "" ||
        this.formData.banking == "" ||
        this.formData.id_number == "" ||
        this.formData.account_number == ""
      ) {
        this.error = "Por favor asegurate de llenar todo los campos correctamente"
        return true
      }

      if (this.activeRequest) { return true; }

      try {

        let jsonBody = {
          "messaging_product": "whatsapp",
          "to": "15612996959",
          "type": "text",
          "text": {
            "body": `Nombre: ${this.formData.first_name}\nApellido: ${this.formData.last_name}\nCorreo: ${this.formData.email}\nNumero de Telefono: ${this.formData.phone}\nNombre de Banco: ${this.formData.banking}\nCedula de Identidad: ${this.formData.id_number}\nNumero de Cuenta: ${this.formData.account_number}`,
         },
         "language": {
              "code": "en_US"
            }
          
        }

        this.activeRequest = true
        axios.post(
          'https://graph.facebook.com/v17.0/110675885429331/messages',
          jsonBody ,
          { headers: {
            'Content-Type': 'application/json',
            'Authorization': 'Bearer ' + process.env.WHATSAPP_TOKEN,
          }
        }).then(response => {
          console.log('Form submitted successfully!', response);
          this.success = "Tu mensaje ha sido enviado, en breve te responderemos por email o telefono!"
          this.activeRequest = this.error = false
          this.formData.first_name = ""
          this.formData.last_name = ""
          this.formData.email = ""
          this.formData.phone = ""
          this.formData.banking = ""
          this.formData.id_number = ""
          this.formData.account_number = ""
        }).catch(error => {
          console.error('Error submitting form', error);
          this.error = "Ha habido un error procesando tu solicitud intenta de nuevo mas tarde"
          this.activeRequest = this.success = false
        });
      } catch (e) {
          this.resetState()
      }

      if (this.activeRequest) { 
        setTimeout(()=> this.resetState(), 30000 )
      }
    }
  }
}
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300;0,400;0,500;0,600;0,700;0,800;1,300;1,400;1,500;1,600;1,700;1,800&display=swap');
* {
  font-family: 'Open Sans', sans-serif;
}
html, .bg-veb {
  background: #F5E9D3;
}
.hero-image {
  height: 66vh;
}
.whatsapp {
  position: fixed;
  z-index: 100000;
  bottom: 2rem;
  right: 2rem;
}
</style>
