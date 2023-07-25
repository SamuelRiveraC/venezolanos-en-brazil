<template>
<div class="Desktop1 w-full flex-col justify-start items-start inline-flex">
  <div class="whatsapp">
    <a href="https://wa.me/+554184290372">
      <img src="WhatsApp.png" alt="" style="width: 64px;">
    </a>
  </div>

  <div class="Navbar self-stretch px-4 md:px-24 py-4 bg-veb justify-between items-center gap-5 inline-flex">
    <div class="text-sky-900 text-2xl font-bold">VENEZOLANOS EN BRAZIL</div>
    <div class="self-stretch px-5 justify-end items-center gap-5 flex" v-if="false">
      <a v-for="link in navbar" :key="link.url" class="text-black text-base font-normal" :href="link.url" > {{ link.name }} </a>
    </div>
  </div>
  <div class="Hero self-stretch px-4 md:px-24 bg-veb grid grid-cols-1 md:grid-cols-2 gap-5">
    <div class="flex flex-col justify-center gap-10">
      <div class="flex text-sky-900 text-4xl font-bold justify-center text-center">
        REALIZA CAMBIOS DE<br/>BOLÍVARES  Y REALES
      </div>
      <div class="flex flex-col items-center rounded-lg gap-5">
        <div class="bg-white p-5 rounded-lg gap-5">
          <div class="grid grid-cols-2 gap-5">
            <div class="flex-col justify-start items-start gap-3 inline-flex">
              <label class="text-sm text-gray-700">Método de Transferencia*</label>
              <select class="border border-solid border-gray-300 rounded-md focus:ring focus:ring-opacity-50 p-1.5 w-full " v-model="formData.tipo">
                <option>Bolivares a Reais</option>
                <option>Reais a Bolivares</option>
              </select>
            </div>
            <div class="flex-col justify-start items-start gap-3 inline-flex" style="position: relative;">
              <span v-if="formData.tipo == 'Bolivares a Reais'" style="position: absolute; bottom: 0; line-height:40px; right: 2rem;">
                Bs$
              </span>
              <span v-if="formData.tipo == 'Reais a Bolivares'" style="position: absolute; bottom: 0; line-height:40px; right: 2rem;">
                R$
              </span>
              <label class="text-sm text-gray-700">Monto a transferir*</label>
              <input type="number" class="border border-solid border-gray-300 rounded-md focus:ring focus:ring-opacity-50 p-1.5 w-full" v-model="formData.monto">
            </div>
            <div class="flex-col justify-start items-start gap-3 inline-flex">
              <label class="text-sm text-gray-700">Titular de la cuenta*</label>
              <input type="text"  class="border border-solid border-gray-300 rounded-md focus:ring focus:ring-opacity-50 p-1.5 w-full " v-model="formData.titular">
            </div>
            <div class="flex-col justify-start items-start gap-3 inline-flex">
              <label class="text-sm text-gray-700">Cedula*</label>        
              <input v-model="formData.cedula" type="text" class="border border-solid border-gray-300 rounded-md focus:ring focus:ring-opacity-50 p-1.5 w-full" maxlength="20">
            </div>
            <div class="flex-col justify-start items-start gap-3 inline-flex">
              <label class="text-sm text-gray-700">Método de pago*</label>
              <select class="border border-solid border-gray-300 rounded-md focus:ring focus:ring-opacity-50 p-1.5 w-full " v-model="formData.metodo">
                <option>Pago movil</option>
                <option>Transferencia bancaria</option>
              </select>
            </div>
            <div class="flex-col justify-start items-start gap-3 inline-flex" v-show="formData.metodo == 'Transferencia bancaria'">
              <label class="text-sm text-gray-700">Numero de cuenta</label>        
              <input v-model="formData.cuenta" type="text" class="border border-solid border-gray-300 rounded-md focus:ring focus:ring-opacity-50 p-1.5 w-full" maxlength="20">
            </div>
            <div class="flex-col justify-start items-start gap-3 inline-flex" v-show="formData.metodo == 'Pago movil'">
              <label class="text-sm text-gray-700">Celular</label>        
              <input v-model="formData.phone" type="text" class="border border-solid border-gray-300 rounded-md focus:ring focus:ring-opacity-50 p-1.5 w-full" maxlength="20">
            </div>
            
            <div class="flex-col justify-start items-start gap-3 inline-flex" style="position: relative;">
              <label class="text-sm text-gray-700">Banco*</label>
              <span @click="()=>this.formData.banco = ''" v-if="formData.banco == 'Otros'" style="position: absolute; bottom: 0; line-height:40px; right: 1rem; font-weight: bold; cursor: pointer;">&#10005;</span>
              <input v-if="formData.banco == 'Otros'" v-model="otrobanco" type="text" class="border border-solid border-gray-300 rounded-md focus:ring focus:ring-opacity-50 p-1.5 w-full">
              <select v-else class="border border-solid border-gray-300 rounded-md focus:ring focus:ring-opacity-50 w-full p-1.5 " v-model="formData.banco">
                <option> 0156 - 100%BANCO</option>
                <option> 0196 - ABN AMRO BANK</option>
                <option> 0172 - BANCAMIGA BANCO MICROFINANCIERO, C.A.</option>
                <option> 0171 - BANCO ACTIVO BANCO COMERCIAL, C.A.</option>
                <option> 0166 - BANCO AGRICOLA</option>
                <option> 0175 - BANCO BICENTENARIO</option>
                <option> 0128 - BANCO CARONI, C.A. BANCO UNIVERSAL</option>
                <option> 0164 - BANCO DE DESARROLLO DEL MICROEMPRESARIO</option>
                <option> 0102 - BANCO DE VENEZUELA S.A.I.C.A.</option>
                <option> 0114 - BANCO DEL CARIBE C.A.</option>
                <option> 0149 - BANCO DEL PUEBLO SOBERANO C.A.</option>
                <option> 0163 - BANCO DEL TESORO</option>
                <option> 0176 - BANCO ESPIRITO SANTO, S.A.</option>
                <option> 0115 - BANCO EXTERIOR C.A.</option>
                <option> 0003 - BANCO INDUSTRIAL DE VENEZUELA.</option>
                <option> 0173 - BANCO INTERNACIONAL DE DESARROLLO, C.A.</option>
                <option> 0105 - BANCO MERCANTIL C.A.</option>
                <option> 0191 - BANCO NACIONAL DE CREDITO</option>
                <option> 0116 - BANCO OCCIDENTAL DE DESCUENTO.</option>
                <option> 0138 - BANCO PLAZA</option>
                <option> 0108 - BANCO PROVINCIAL BBVA</option>
                <option> 0104 - BANCO VENEZOLANO DE CREDITO S.A.</option>
                <option> 0168 - BANCRECER S.A. BANCO DE DESARROLLO</option>
                <option> 0134 - BANESCO BANCO UNIVERSAL</option>  
                <option> 0177 - BANFANB</option>
                <option> 0146 - BANGENTE</option>
                <option> 0174 - BANPLUS BANCO COMERCIAL C.A</option>
                <option> 0190 - CITIBANK.</option>
                <option> 0121 - CORP BANCA.</option>
                <option> 0157 - DELSUR BANCO UNIVERSAL</option>
                <option> 0151 - FONDO COMUN</option>
                <option> 0601 - INSTITUTO MUNICIPAL DE CR&#201;DITO POPULAR</option>
                <option> 0169 - MIBANCO BANCO DE DESARROLLO, C.A.</option>
                <option> 0137 - SOFITASA</option>
                <option>Otros</option>
              </select>
            </div>

            <div class="flex-col justify-start items-start gap-3 inline-flex">
              <label class="text-sm text-gray-700">WhatsApp de contacto*</label>
              <vue-tel-input v-model="formData.whatsapp" mode="international" class="border border-solid border-gray-300 rounded-md focus:ring focus:ring-opacity-50 p-1.5 w-full"></vue-tel-input>
            </div>

            <div class="col-span-2 bg-green-500 p-4 text-white" v-if="success">
              <p>
                {{ success }}
              </p>
              <a href="https://wa.me/+554184290372" style="text-decoration: underline; font-weight: bold;">
                Contactanos por Whatsapp a este numero
              </a>
            </div>
            <div class="col-span-2 bg-red-500 p-4 text-white" v-if="error">
              {{ error }}
            </div>
            <div class="col-span-2 flex-col justify-center items-center gap-5 flex">
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
<style src="vue-tel-input/dist/vue-tel-input.css"></style>
<script>
import axios from "axios"
import { VueTelInput } from 'vue-tel-input';
export default {
  name: 'IndexPage',
  components: { VueTelInput },
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
      formData: {
        tipo: "Bolivares a Reais",
        monto: "0",
        titular: "",
        banco: "",
        metodo: "Pago movil",
        cuenta: "",
        phone: "",
        cedula: "",
        whatsapp: "",
      },
      otrobanco: "",
      error: false,
      success: false,
    }
  },
  
  computed: {
    finalPrice () {
      let currency = "";
      if (this.formData.tipo == 'Bolivares a Reais') currency = "Bs$" 
      if (this.formData.tipo == 'Reais a Bolivares') currency = "R$" 
      return `${this.formData.monto} ${currency}`
    },
    whatsapp_phone () {
      let phone = this.formData.whatsapp
      phone = phone.replace(' ','')
      return `https://wa.me/${phone}`
    },
    finalBanco () {
      if (this.formData.banco == "Otros") return this.otrobanco
      return this.formData.banco
    }
  },
  methods: {
    resetState () {
      this.activeRequest = this.error = this.success = false
    },
    submitForm() {
      let finalMessage = `METODO DE TRANSFERENCIA: ${this.formData.tipo}\nMONTO A TRANSFERIR: ${this.finalPrice} \nTITULAR DE LA CUENTA: ${this.formData.titular}\nBANCO: ${this.finalBanco}\nMETODO DE PAGO: ${this.formData.metodo}\nNUMERO DE CUENTA: ${this.formData.cuenta}\nCEDULA DE IDENTIDAD: ${this.formData.cedula}\nCELULAR: ${this.formData.phone}\nWHATSAPP DE CONTACTO: ${this.whatsapp_phone}`
      console.log(finalMessage)
      if (
        this.formData.tipo == "" ||
        this.formData.monto == "" ||
        this.formData.titular == "" ||
        this.formData.banco == "" ||
        this.formData.metodo == "" ||
        this.formData.cedula == "" ||
        this.formData.whatsapp == ""
      ) {
        this.error = "Por favor asegurate de llenar todo los campos correctamente"
        return true
      }

      if (this.activeRequest) { return true; }

      try {
        let jsonBody = {
          "messaging_product": "whatsapp",
          "to": "554184290372",
          "type": "text",
          "text": {
            "body": finalMessage,
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
            'Authorization': 'Bearer EAAEOkRRwhsoBAGHGTYPpya5hzih5ukq8cGmXz5WicguKLBAGPDPWVZBEyYFHVBHH33OfL2evBL3uZAdSspVxBoI69XJjNQzVd4REnXpkgeAuGEy3I70KDP34EdmRtVEQcRvDQpPX4kw0XRjJukjO68cLvs5TM5gyUbfpiZBoBnZBOBGTNTo7oGrgrPDnJJVnvdkgcjSt8wZDZ',
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
.vue-tel-input {
  padding: 0;
}
</style>
