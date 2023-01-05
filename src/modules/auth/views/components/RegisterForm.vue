<template>
  <div class="w-full">
    <el-card class="bg-secondary text-center">
      <div class="content-center items-center w-full lg:p-6">
        <div class="text-muted text-center mb-5">
          <small> Sign up with credentials </small>
        </div>
        <el-form ref="form" :model="formData" class="authentication-form pb-6" :rules="formRules">
          <!-- name -->
          <el-form-item class="mb-6 rounded-md" prop="name">
            <div
              class="authentication-form-icon z-10 absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none"
            >
              <div class="w-5 h-5">
                <AcademicCapIcon class="w-5 h-5 text-gray-210" />
              </div>
            </div>
            <el-input placeholder="Name" v-model="formData.name" />
          </el-form-item>

          <!-- email -->
          <el-form-item class="mb-6 rounded-md" prop="email" >
            <div
              class="authentication-form-icon z-10 absolute inset-y-0 left-0 pl-2.5 flex items-center pointer-events-none"
            >
              <div class="w-5 h-5">
                <MailIcon class="w-5 h-5 text-gray-210" />
              </div>
            </div>
            <el-input type="email" placeholder="Email" v-model="formData.email"/>
          </el-form-item>

          
          <!-- <el-form-item class="mb-6 rounded-md" prop="password">
            <div
              class="authentication-form-icon z-10 absolute inset-y-0 left-0 pl-2.5 flex items-center pointer-events-none"
            >
              <div class="w-5 h-5">
                <LockOpenIcon class="w-5 h-5 text-gray-210" />
              </div>
            </div>
            <el-input type="password" placeholder="Confirm Password" v-model="formData.password" />
          </el-form-item>
          <el-form-item class="mb-6 rounded-md">
            <div class="italic">
              <span class="text-0.8125 text-muted font-normal">
                password strength: <strong class="text-success">strong</strong>
              </span>
            </div>
          </el-form-item>
          <el-form-item class="mb-6">
            <el-checkbox class="w-4 h-4 text-muted font-normal"
              >I agree with the
              <a href="#!" class="text-indigo-410 hover:text-indigo-410-active">Privacy Policy</a>
            </el-checkbox>
          </el-form-item> -->
        </el-form>
        <el-button type="primary" @click="register"> Create account </el-button>
      </div>
    </el-card>
  </div>
</template>
<script lang="ts">
import { defineComponent, ref, reactive } from 'vue'
import { MailIcon, AcademicCapIcon, IdentificationIcon, LockOpenIcon } from '@heroicons/vue/solid'

export default defineComponent({
  name: 'RegisterForm',
  components: {
    MailIcon,
    AcademicCapIcon,
    IdentificationIcon,
    LockOpenIcon,
  },
  setup() {
    const form = ref<ElementForm>()
    const formData = ref({
      name:'',
      email:'',
      password:'',
      status:'',
      religion:'',
      gender:'',
      phone:'',
      citizen:'',
      instagram:'',
      linkedin:'',
      website:'',
      desc:'',
      language:'',
      github:'',
    })
    const formRules = {
          name:[{required:true, message:'Wajib Diisi'}],
          email:[{required:true, message:'Wajib Diisi'}],
        }
    const userReligion = [
      {
        id:1,
        nameType: 'Islam',
      },
      {
        id:2,
        nameType: 'Kristen',
      },
      {
        id:3,
        nameType: 'Hindu',
      },
      {
        id:4,
        nameType: 'Budha',
      },
      {
        id:5,
        nameType: 'Konghucu',
      },
    ]

    const userGender =[
      {
        id:1,
        genderType:'Laki-Laki',
      },
      {
        id:2,
        genderType:'Perempuan',
      },
    ]

    const register = async () => {
      try {
        console.log(formData.value);
        
        // if (!store.auth.isAuthenticated) {
        //   store.auth.actLogin(formData.value)
        // }
      } catch (e) {
        console.log('err::: ', e)
      }
    }

    return {
      formRules,
      register,
      userGender,
      userReligion,
      form,
      formData,
    }
  },
})
</script>

<style lang="scss" scoped>
.item-input-popper {
  .el-select-dropdown__item.selected {
    @apply text-indigo-410;
  }
}
</style>
