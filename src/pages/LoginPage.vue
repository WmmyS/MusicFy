<template>
  <q-page class="container bg-grey-11" padding>
    <p class="text-h4">Login de Usuário</p>
    <div class="q-col-gutter-md">
      <q-form ref="myForm"
      @submit="onSubmit"
      @reset="onReset"
      class="row q-col-gutter-md"

      >
        <q-input
          outlined
          rounded
          clearable
          clear-icon="cancel"
          bg-color="grey-1"
          v-model= "form.user"
          color="orange-10"
          label="Usuário"
          class="col-md-12 col-sm-12 col-xs-12"
          :rules="[
            value => value && value.length > 0 || 'Usuário obrigatório'
          ]"
          hint="Insira seu usuário de login"
        >
          <template v-slot:prepend>
            <q-icon name="account_circle" />
          </template>
        </q-input>

        <q-input
        outlined
        rounded
        bg-color="grey-1"
        v-model="form.password"
        color="orange-10"
        label="Senha"
        class="col-md-12 col-sm-12 col-xs-12"
        :type="form.isPwd ? 'password' : 'text'"
        :rules="[
          value => value && value.length > 0 || 'Senha obrigatória'
        ]"
        hint="Insira sua senha"

        >
          <template v-slot:append>
            <q-icon
              :name="form.isPwd ? 'visibility_off' : 'visibility'"
              class="cursor-pointer"
              @click="form.isPwd = !form.isPwd"
            />
          </template>
          <template v-slot:prepend>
            <q-icon name="lock" />
          </template>
        </q-input>

        <div>
          <q-btn
          label="Login"
          type="submit"
          color="orange-10"
          :size='"md"'
          rounded
          class= "q-ml-sm"
          />
          <q-btn
          label="Reset"
          type="reset"
          color="orange-10"
          :size='"md"'
          rounded
          flat class="q-ml-sm" />
        </div>

      </q-form>
    </div>

      <p>{{ form.user }} </p>
      <p>{{ form.password }}</p>

  </q-page>
</template>

<script lang="ts">
import { ref } from 'vue';
import { useQuasar } from  'quasar'

export default ({
  name: 'LoginPage',

  data() {
    const $q = useQuasar();

    return {
      form: {
        user: '',
        password: '',
        isPwd: ref(true),
      },

      onSubmit () {
        $q.notify({
          message: 'Login efetuado com sucesso',
          color: 'positive',
          icon: 'check_circle_outline',
        })
        console.log('submit');
      },

      onReset() {
        console.log('Reset');
      },

      methods: {}
    }
  }





})

</script>
