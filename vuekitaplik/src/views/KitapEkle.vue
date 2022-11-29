<template>
  <div class="col-md-6 offset-sm-1 offset-md-2">
    <table class="table table-striped table-hover">
      <tbody>
        <tr>
          <td>Kitap Adı:</td>
          <td><input type="text" class="form-control bg-light" v-model="kitapAdi"></td>
        </tr>
        <tr>
          <td>Yazarı:</td>
          <td><input type="text" class="form-control bg-light" v-model="yazari"></td>
        </tr>
      </tbody>
      <tfoot>
        <tr>
          <td colspan="2"><button class="btn btn-success" @click="kitapEkle()">Ekle</button></td>
        </tr>
      </tfoot>

    </table>
  </div>
</template>
<script>
export default {
  data() {
    return {
      kitapAdi: "",
      yazari: ""
    }
  },
  methods: {
    kitapEkle() {
      let kitap = {
        kitapAdi: this.kitapAdi,
        yazari: this.yazari,
        id: Math.floor(Math.random()*10000) + "-" + Math.floor(Math.random()*1000)
      }
      fetch("http://localhost:3000/kitaplar", {
        method: "POST",
        headers: { "Content-type": "application/json" },
        body: JSON.stringify(kitap)
      }).then(()=>console.log(kitap)).then(()=>this.$router.push("/"))
    }
  }
}
</script>

<style>

</style>
