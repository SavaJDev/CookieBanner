<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12"> 
              <v-snackbar class="content"
                          v-model="snackbar" 
                          transition="slide-y-reverse-transition"
                          :timeout="-1" 
                          light>
             <p>{{ contentSnackbar }}</p> 
             <v-row>
                <div
                  class="btn-details"
                  @click="details=!details"
                >
                    {{ btnDetails }} 
                <v-icon class="mdi" :class="[details ? 'mdi-chevron-up' : 'mdi-chevron-down']" :color="'#4742c9'"></v-icon>
                </div> 
                <v-spacer></v-spacer>        
                <v-btn
                 class="btnOk"
                 :elevation="0"
                 :width="70"
                 x-small
                 rounded
                 @click="snackbar = false"
                >
                  OK
                </v-btn> 
             </v-row>     
           </v-snackbar>    
      </v-col>
    </v-row>  
  </v-container>
</template>

<script>
  export default {
    name: 'CookieBanner',

    data: () => ({
       snackbar: false,
       text: 'Мы используем файлы cookie на нашем веб-сайте. Файлы cookie используются для улучшения функциональности и                 использования нашего сайта, а также для целей аналитики. Разрешение на использование cookie необходимо для                 использования Сайта и его сервисов, включая заказ услуг. Мы уверены, что при посещении страниц сайта вы                   даётесогласие на использование и хранение     файлов cookie на вашем устройстве. Если согласны, продолжайте               пользоваться сайтом. Если нет - установите специальные настройки в браузере или обратитесь в техподдержку.',
       details: false
    }),
    computed: {
        contentSnackbar() {
            if(this.details){
                return this.text
            }
            else {
                let str = this.text.slice(0, 178)
                return str
            }
            
        },
        btnDetails() {
            let txt = this.details ? 'Свернуть' : 'Подробнее'
            return txt;
        }
    },
    mounted() {
        setTimeout(() => this.snackbar = true, 2000);
    }  
  }
</script>


<style>
    .content .v-snack__wrapper {
        width: 100%;
        min-width: 315px;
        max-width: none;
        min-height: 60px;
        border: 1px solid #4742c9;
        margin: 0;
    }
    
    .btn-details {
        cursor: pointer;
        color: #4742c9;
        padding-left: 16px;
    }
    
    .btnOk {
        background: #4742c9 !important;
        color: white !important;  
        
    }
</style>