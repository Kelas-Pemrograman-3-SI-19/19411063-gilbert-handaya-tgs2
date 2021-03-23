<template>
  <div class="q-pa-md" style="max-width: 300px">
    <form @submit.prevent.stop="onSubmit" @reset.prevent.stop="onReset" class="q-gutter-md">
      <q-input
          ref="nama"
          filled
          v-model="form.nama"
          label="Nama Lengkap"
          hint="Nama Lengkap"
          lazy-rules
          :rules="[ val => val && val.length > 0 || 'Masukkan Nama Lengkap Anda']"
      />

      <q-input
          ref="nomor"
          filled
          type="number"
          v-model="form.nomor"
          label="Nomor Telpon"
          lazy-rules
          :rules="[
          val => val && val.length > 0 || 'Masukkan Nomor yang sesuai'
        ]"
      />

      <q-input
          ref="hobi"
          filled
          v-model="form.hobi"
          label="Hobi"
          lazy-rules
          :rules="[ val => val && val.length > 0 || 'Masukkan Hobi Anda']"
      />

      <q-input
          ref= "umur"
          filled
          v-model="form.umur"
          label="Umur"
          lazy-rules
          :rules="[
          val => val !== null && val !== '' || 'Please type your age',
          val => val > 0 && val < 100 || 'Please type a real age'
        ]"
      />

      <q-toggle v-model="accept" label="I accept the license and terms" />

      <div>
        <q-btn label="Submit" type="submit" color="primary" />
        <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" />
      </div>
      <div>
        {{ label="Nama Anda : "+datas.nama }}<br>
        {{ label="Nomor Telpon : "+datas.nomor}}<br>
        {{ label="Hobi Anda : "+datas.hobi}}<br>
        {{ label="Umur Anda : "+datas.nomor}}<br>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data () {
    return {
      form: {
        nama: null,
        nomor: null,
        hobi: null,
        umur: null
      },
      datas: {
        nama: null,
        nomor: null,
        hobi: null,
        umur: null
      },
      accept: false
    }
  },

  methods: {
    onSubmit () {
      this.datas = this.form
      console.log(this.datas)
    },

    onReset () {
      this.form.nama = null
      this.form.umur = null
      this.form.hobi = null
      this.form.nomor = null

      this.$refs.name.resetValidation()
      this.$refs.age.resetValidation()
    }
  }
}
</script>
