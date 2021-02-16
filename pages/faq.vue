<template>
  <div class="p-12">
    <div class="text-2xl font-semibold ">Pertanyaan yang sering ditanyakan</div>
    <div v-for="(data,index) in data" :key="index">
      <div class="my-6">
        <button class="flex w-full rounded-md shadow-lg focus:outline-none hover:bg-gray-200 bg-white p-6 mx-4" @click="toggle(index)">
          <div class="flex">
              <div class="p-2 mr-4 font-bold text-xl">
                  {{ data.id }}
              </div>
              <div class="p-2 font-bold text-xl">
                  {{ data.title }}
              </div>

          </div>
        </button>
        <div  v-show="data.flag" class="flex w-full rounded shadow-md bg-white p-6 mx-4 hover:bg-gray-200" >
          {{ data.body }}
        </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return{
      open: false,
      data:[
        {
          id    :1,
          title : 'Apa itu Novel Coronavirus (2019-nCoV)?',
          body :`Novel coronavirus (2019-nCoV) adalah jenis baru coronavirus yang belum pernah diidentifikasi sebelumnya pada manusia. Coronavirus merupakan keluarga besar virus yang menyebabkan penyakit pada manusia dan hewan. Pada manusia menyebabkan penyakit mulai flu biasa hingga penyakit yang serius seperti Middle East Respiratory Syndrome (MERS) dan Sindrom Pernapasan Akut Berat/ Severe Acute Respiratory Syndrome (SARS).
                Pada 11 Februari 2020, World Health Organization (WHO) mengumumkan nama penyakit yang disebabkan 2019-nCov, yaitu Coronavirus Disease (COVID-19).`,
            flag :false
        },
         {
          id    :2,
          title : 'Bagaimana cara mencegah penularan COVID-19?',
          body :`Hingga saat ini, belum ada vaksin untuk mencegah penularan COVID-19.
                  Salah satu cara yang bisa dilakukan untuk mencegah tertularnya virus ini adalah:
                  Menjaga kesehatan dan kebugaran agar sistem imunitas/ kekebalan tubuh meningkat.
                  Mencuci tangan menggunakan air dan sabun atau  hand-rub berbasis alkohol. Mencuci tangan sampai bersih selain dapat membunuh virus yang mungkin ada di tangan kita, tindakan ini juga merupakan salah satu tindakan yang mudah dan murah. Sekitar 98% penyebaran penyakit bersumber dari tangan. Karena itu, menjaga kebersihan tangan adalah hal yang sangat penting.
                  Ketika batuk dan bersin, upayakan menjaga agar lingkungan Anda tidak tertular. Tutup hidung dan mulut Anda dengan tisu atau dengan lengan (bukan dengan telapak tangan).
                  Menjaga jarak saat berbicara dengan orang lain, sekurang- kurangnya satu meter, terutama dengan orang yang sedang menderita batuk, pilek/bersin dan demam. Saat seseorang terinfeksi penyakit saluran pernafasan, seperti 2019-nCoV, batuk/bersin dapat menghasilkan droplet yang mengandung virus. Jika kita terlalu dekat, virus tersebut dapat terhirup oleh kita.
                  Hindari menyentuh mata, hidung dan mulut. Tangan menyentuh banyak hal yang dapat terkontaminasi virus. Jika kita menyentuh mata, hidung dan mulut dengan tangan yang terkontaminasi, maka virus dapat dengan mudah masuk ke tubuh kita.
                  Gunakan masker penutup mulut dan hidung ketika Anda sakit atau saat berada di tempat umum.
                  Buang tisu dan masker yang sudah digunakan ke tempat sampah, lalu cucilah tangan Anda.
                  Hindari kontak dengan hewan ternak dan hewan liar yang terbukti tertular coronavirus.
                  Jangan makan daging yang tidak dimasak hingga matang.
                  Menunda perjalanan ke daerah/negara dimana virus ini ditemukan seperti Tiongkok, seiring dengan informasi adanya penghentian sementara operasional penerbangan langsung dari dan ke daratan Cina dari pemerintah, sampai ada informasi lebih lanjut.`,
          flag:false,
                          },
             {
          id    :3,
          title : 'Apa saja gejala COVID-19?',
          body :`Gejala umum berupa demam ≥38C, batuk, pilek, nyeri tenggorokan dan sesak napas. Jika ada orang dengan gejala tersebut pernah melakukan perjalanan ke Tiongkok (terutama Wuhan), atau pernah merawat/kontak dengan penderita COVID-19, maka terhadap orang tersebut akan dilakukan pemeriksaan laboratorium lebih lanjut untuk memastikan diagnosisnya.`,
            flag :false
        },
         {
          id    :4,
          title : 'Seberapa bahaya COVID-19 ini?',
          body :`Seperti penyakit pernapasan lainnya, infeksi 2019-nCoV dapat menyebabkan gejala ringan termasuk pilek, sakit tenggorokan, batuk, dan demam. Beberapa orang mungkin akan menderita sakit yang parah, seperti disertai pneumonia atau kesulitan bernafas. Walaupun fatalitas penyakit ini masih jarang, namun bagi orang yang berusia lanjut, dan orang-orang dengan kondisi medis yang sudah ada sebelumnya (seperti, diabetes dan penyakit jantung), mereka biasanya lebih rentan untuk menjadi sakit parah.`,
            flag :false
        },
          {
          id    :5,
          title : 'Bagaimana manusia bisa terinfeksi COVID-19?',
          body :`Sampai saat ini, belum diketahui bagaimana manusia bisa terinfeksi virus ini. Para ahli masih sedang melakukan penyelidikan untuk menentukan sumber virus, jenis paparan, cara penularan dan pola klinis serta perjalanan penyakit. Hasil penyelidikan sementara dari beberapa institusi di kota Wuhan, sebagian kasus terjadi pada orang yang bekerja di pasar hewan/ikan, namun belum dapat dipastikan jenis hewan penular virus ini. Hingga saat ini dilaporkan adanya penularan antar manusia yang terbatas (antar keluarga dekat dan petugas kesehatan yang merawat kasus).`,
            flag :false
        },


      ]

    }
  },
  methods:{
     	toggle(index) {
         console.log(index)
         for (var i = 0; i < this.data.length; i++) {
        if (this.data[index] === this.data[i]) {
          this.data[index].flag = !this.data[index].flag;
        } else {
          this.data[i].flag = false;
        }
      }
    }
  }

}
</script>

<style>

</style>