<template>
  <q-page class="container bg-grey-11" padding>
  <div class="q-col-gutter-md">
    <p class="text-h5">Login de Usuário</p>
    <q-form
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
        color="orange-10"
        label="Usuário"
        class="col-md-12 col-sm-12 col-xs-12"
        v-model="user"
        hint="Insira seu usuário de login"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Usuário obrigatório']"
      >
        <template v-slot:prepend>
            <q-icon name="account_circle" />
        </template>

      </q-input>

      <q-input
        outlined
        rounded
        bg-color="grey-1"
        v-model="password"
        color="orange-10"
        label="Senha"
        class="col-md-12 col-sm-12 col-xs-12"
        :type="isPwd ? 'password' : 'text'"
        hint="Insira sua senha"
        :rules="[
          value => value && value.length > 0 || 'Senha obrigatória',
        ]"
      >
          <template v-slot:append>
            <q-icon
              :name="isPwd ? 'visibility_off' : 'visibility'"
              class="cursor-pointer"
              @click="isPwd = !isPwd"
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
  </q-page>
</template>

<script lang="ts">
import { useQuasar } from 'quasar'
import { ref } from 'vue'

export default {
  setup () {
    const $q = useQuasar()

    const user = ref(null)
    const password = ref(null)
    const isPwd = ref(true)

    return {
      user,
      password,
      isPwd,

      onSubmit () {
         if (user.value !== 'wesley' || password.value !== 'senha' ) {
           $q.notify({
            color: 'red-5',
            textColor: 'white',
            icon: 'warning',
            message: 'Usuário ou senha inválida'
          })
        } else {
          $q.notify({
          color: 'green-4',
          textColor: 'white',
          icon: 'cloud_done',
          message: 'Entrando'
        })
        }
      },

      onReset () {
        user.value = null
        password.value = null
        isPwd.value = true
      }
    }
  },
  methods: {
  }
}
</script>
