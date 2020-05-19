<template>
  <v-app>
    <v-app-bar app> </v-app-bar>
    <v-navigation-drawer app> </v-navigation-drawer>

    <v-content>
      <v-form ref="formPendaftaran" v-model="isvalid" lazy-validation>
        <v-card>

          <v-card-title>
            Form Pendaftaran Mahasiswa
          </v-card-title>

          <v-card-text>

            <v-text-field v-model="namaMhs" :rules="rule_nama_mhs" label="Nama Mahasiswa" outlined></v-text-field>
            <v-radio-group v-model="jk" row>
              <v-radio label="Laki - laki" value="L"></v-radio>
              <v-radio label="Perempuan" value="P"></v-radio>
            </v-radio-group>

            <v-select v-model="kode_prodi" :rules="rule_kode_prodi" label="Program Studi" :items="daftar_prodi" outlined=""></v-select>

          </v-card-text>

          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="indigo" dark @click="simpanMahasiswaBaru">Simpan</v-btn>
          </v-card-actions>
        </v-card>
      </v-form>
    </v-content>
  </v-app>
</template>

<script>
export default {
  data()
  {
    return {
      isvalid:true,
      namaMhs:'',
      jk:'L',
      daftar_prodi:[
        {
          text: 'Teknik Informatika',
          value: 'Teknik Informatika'
        },
        {
          text: 'Sistem Informasi',
          value: 'Sistem Informasi'
        },
        {
          text: 'Komputer Akutansi',
          value: 'Komputer Akutansi'
        }
      ],
      kode_prodi:'',

      rule_nama_mhs:[
        value => !!value || "nama mahasiswa harap di isi"
      ],
      rule_kode_prodi:[
        value => !!value || "harap di isi"
      ]
    }
  },

  methods: {
      simpanMahasiswaBaru ()
      {
        if (this.$refs.formPendaftaran.validate())
        {
          console.log('Nama Mahsiswa', this.namaMhs);
          console.log('Jenis Kelamin', this.jk);
          console.log('Program Studi', this.kode_prodi);
        }
      }
  },


wacth:{
//     kode_prodi(val)
//     {
//       console.log(val);
//     }
  }
}
</script>

<style scoped>

</style>
