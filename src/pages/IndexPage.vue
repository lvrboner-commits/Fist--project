<template>
  <q-page class="flex flex-center">
    <q-card class="my-card q-pa-md" style="width: 400px">
      <q-card-section>
        <div class="text-h6 text-primary text-center">ฟอร์มบันทึกข้อมูลของฉัน</div>
      </q-card-section>

      <q-form @submit="onSubmit" class="q-gutter-md">
        <q-input v-model="name" label="ชื่อ-นามสกุล" outlined required />
        <q-input v-model="age" type="number" label="อายุ" outlined required />
        <q-checkbox v-model="accept" label="ฉันยอมรับเงื่อนไขข้อตกลงและนโยบายความเป็นส่วนตัว" />
        
        <div class="text-center q-mt-md">
          <q-btn label="ส่งข้อมูล" type="submit" color="primary" class="full-width"/>
        </div>
      </q-form>
    </q-card>
  </q-page>
</template>

<script>
import { useQuasar } from 'quasar'
import { ref } from 'vue'

export default {
  setup () {
    const $q = useQuasar()

    const name = ref(null)
    const age = ref(null)
    const accept = ref(false)

    return {
      name,
      age,
      accept,

      onSubmit () {
        if (accept.value !== true) {
          $q.notify({
            color: 'red-5',
            textColor: 'white',
            icon: 'warning',
            message: 'กรุณาติ๊กยอมรับเงื่อนไขก่อนดำเนินการต่อ'
          })
        } else {
          $q.notify({
            color: 'green-4',
            textColor: 'white',
            icon: 'cloud_done',
            message: 'บันทึกข้อมูลเรียบร้อยแล้ว'
          })
        }
      }
    }
  }
}
</script>
