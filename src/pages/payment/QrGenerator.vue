<template>
  <q-page padding>
    <!-- content -->
    <div class="row justify-center q-mt-xl">
			<qrcode-vue :value="list.toString()" :size="size" level="H"></qrcode-vue>
    </div>
  </q-page>
</template>

<script>
import QrcodeVue from 'qrcode.vue'
export default {
  // name: 'PageName',
  data () {
    return {
      value: '',
      list: [
        {produto: 'Manga', preco: 30},
        {produto: 'Banana', preco: 24},
        {produto: 'Compara 2L', preco: 60}
      ],
      size: 250,
    }
  },
  components: {
    QrcodeVue
  },
  mounted () {
    console.log('nelzio')
    let price = []
    let produto = []
    for(var i in this.list){
      price.push(this.list[i].preco)
      produto.push(this.list[i].produto)
    }
    let strPrice = price.toString()
    let strProd = produto.toString()
    let ar = []
    for(let n in strProd.split(",")){
      ar.push({produto: strProd.split(",")[n], preco: parseInt(strPrice.split(",")[n])})
    }
    console.log(ar)
  }
}
</script>

<style>
</style>
