<template>
  <v-app>
    <div class="background">
      <svg class="custom-shape-divider-bottom-1655409466" data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 120" preserveAspectRatio="none">
        <path fill="#9013FE" d="M0,0V46.29c47.79,22.2,103.59,32.17,158,28,70.36-5.37,136.33-33.31,206.8-37.5C438.64,32.43,512.34,53.67,583,72.05c69.27,18,138.3,24.88,209.4,13.08,36.15-6,69.85-17.84,104.45-29.34C989.49,25,1113-14.29,1200,52.47V0Z" opacity=".25" class="shape-fill"></path>
        <path d="M0,0V15.81C13,36.92,27.64,56.86,47.69,72.05,99.41,111.27,165,111,224.58,91.58c31.15-10.15,60.09-26.07,89.67-39.8,40.92-19,84.73-46,130.83-49.67,36.26-2.85,70.9,9.42,98.6,31.56,31.77,25.39,62.32,62,103.63,73,40.44,10.79,81.35-6.69,119.13-24.28s75.16-39,116.92-43.05c59.73-5.85,113.28,22.88,168.9,38.84,30.2,8.66,59,6.17,87.09-7.5,22.43-10.89,48-26.93,60.65-49.24V0Z" opacity=".5" class="shape-fill"></path>
        <path d="M0,0V5.63C149.93,59,314.09,71.32,475.83,42.57c43-7.64,84.23-20.12,127.61-26.46,59-8.63,112.48,12.24,165.56,35.4C827.93,77.22,886,95.24,951.2,90c86.53-7,172.46-45.71,248.8-84.81V0Z" class="shape-fill"></path>
    </svg>
    </div>
    <v-main class="d-flex justify-center align-center">
      <v-col cols="10" lg="3" class="mx-auto">
        <v-card class="pa-4 rounded-lg">
          <div class="text-center">
            <v-avatar size="100" color="indigo lighten-2">
              <v-icon size="40" color="#9013FE">mdi-account</v-icon>
            </v-avatar>
            <h2 class="indigo--text">Login</h2>
          </div>
          <v-form @submit.prevent="submitHandler" ref="form">
            <v-card-text>
              <v-text-field 
              v-model="email"
              :rules="emailRules"
              type="email"
              label="Email"
              placeholder="Email"
              prepend-inner-icon="mdi-account"
              />
               <v-text-field 
               v-model="password"
              :rules="passwordRules"
              :type="passwordShow?'text':'password'"
              label="Senha"
              placeholder="Senha"
              prepend-inner-icon="mdi-key"
              :append-icon="passwordShow ? 'mdi-eye' : 'mdi-eye-off'"
              @click:append="passwordShow = !passwordShow"
              />
              <v-switch label="Manter login" color="#9013FE"></v-switch>
            </v-card-text>
            <v-card-actions class="justify-center">
              <v-btn :loading="loading" type="submit" color="#9013FE">
                <span class="white--text px-8">Logar</span>
              </v-btn>
            </v-card-actions>
          </v-form>
        </v-card>
      </v-col>
    </v-main>
    <v-snackbar top color="#9013FE" v-model="snackbar">
      Logado com sucesso!
    </v-snackbar>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    loading:false,
    snackbar: false,
    passwordShow:false,
    password: '',
      passwordRules: [
        v => !!v || 'Senha requerida',
        v => (v && v.length >= 6) || 'A senha deve conter 6 ou mais caracteres',
      ],
      email: '',
      emailRules: [
        v => !!v || 'Informe o E-mail',
        v => /.+@.+\..+/.test(v) || 'E-mail deve ser válido',
      ],
  }),
  methods:{
    submitHandler(){
      if(this.$refs.form.validate()){
        this.loading = true
        setTimeout(()=>{
          this.loading = false
          this.snackbar = true
        }, 3000)
      }
    }
  }
};
</script>

<style>
  .background{
    background-image: linear-gradient(to bottom, #9013fe, #ac09f9, #c403f5, #d806f0, #eb12eb);
    height: 100%;
    width: 100%;
    display: block;
    position: absolute;
    top: 0;
    background-size: cover;
  }
  .custom-shape-divider-bottom-1655409466 {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    overflow: hidden;
    line-height: 0;
    transform: rotate(180deg);
}

.custom-shape-divider-bottom-1655409466 svg {
    position: relative;
    display: block;
    width: calc(122% + 1.3px);
    height: 233px;
}

.custom-shape-divider-bottom-1655409466 .shape-fill {
    fill: #9013FE;
}
</style>