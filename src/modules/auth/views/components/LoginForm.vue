<template>
  <div class="w-full">
    <el-card class="bg-secondary text-center pb-6">
      <template #header>
        <div class="text-muted text-center mt-2 mb-4">
          <small class="text-90">Sign in</small>
        </div>
      </template>
      <div class="content-center items-center w-full lg:p-6">
        <div class="mb-4 mt-2 text-center">
          <small class="block w-full text-12.8 mb-6 text-muted">{{ description }}</small>
        </div>
        <el-form ref="form" :model="formData" class="authentication-form">
          <el-form-item class="warning-input mb-4 rounded-md" prop="email">
            <div class="z-10 absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
              <div class="w-5 h-5">
                <MailIcon class="w-5 h-5 text-gray-210" />
              </div>
            </div>
            <el-input placeholder="Email" name="email" v-model="formData.email"/>
          </el-form-item>
          <el-form-item class="mb-6 rounded-md" prop="password">
            <div class="z-10 absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
              <div class="w-5 h-5">
                <LockOpenIcon class="w-5 h-5 text-gray-210" />
              </div>
            </div>
            <el-input type="password" placeholder="Password" name="password" v-model="formData.password"/>
          </el-form-item>
        </el-form>
        <el-button type="primary" @click="handleLoginClick"> Sign in </el-button>
        
      </div>
    </el-card>
  </div>
</template>
<script lang="ts">
import { defineComponent, ref } from 'vue'
import useStore from 'store'
import { MailIcon, LockOpenIcon } from '@heroicons/vue/solid'

export default defineComponent({
  name: 'LoginForm',
  components: {
    MailIcon,
    LockOpenIcon,
  },
  props: {
    height: {
      type: Number,
    },
    description: {
      type: String,
      default: '',
    },
    email: {
      type: String,
      default: '',
    },
    password: {
      type: String,
      default: '',
    },
  },
  setup(props) {
    const store = useStore()
    const form = ref<ElementForm>()
    const formData = ref({ email: "", password: "" })

    const handleKeyDown = async () => {
      login()
    }

    const handleLoginClick = async () => {
      login()
    }

    const login = async () => {
      try {
        console.log(formData.value.email);
        
        // if (!store.auth.isAuthenticated) {
        //   store.auth.actLogin(formData.value)
        // }
      } catch (e) {
        console.log('err::: ', e)
      }
    }
    return {
      form,
      formData,
      handleLoginClick,
      handleKeyDown,
    }
  },
})
</script>
