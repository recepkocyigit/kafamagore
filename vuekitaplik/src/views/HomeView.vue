<template>
  <div class="home">
    <h2> Home </h2>
    <button @click="yenile()">Yenile</button>
    <div v-for="kitap in kitaplar" :key="kitap.id">
      <span>{{ kitap.kitapAdi }}</span>&nbsp;<span>{{ kitap.yazari }}</span>
    </div>
  </div>
</template>

<script>

export default {
  name: 'HomeView',
  data() {
    return {
      kitaplar: []
    }
  },
  methods: {
    yenile() {
      
    }

  },
  mounted() {
    fetch("http://localhost:3000/kitaplar")
      .then((resp) => resp.json())
      .then((data) => this.kitaplar = data)
      .catch((err) => console.log(err))
  }
      

}
</script>
