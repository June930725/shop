<template lang="pug">
  #home
    b-row
      b-col(cols="12" md="6" lg="3" v-for="(item, index) in items" :key="index")
        b-card(:title="item.name" :img-src="item.img" img-top :sub-title="'$'+item.price")
          b-button(variant="primary" @click="addCart(item)")
            font-awesome-icon(:icon="['fas', 'shopping-basket']")
            | &nbsp;放入購物籃
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      items: [
        {
          name: '來一客_川辣牛肉風味',
          img: 'https://e.ecimg.tw/items/DBAAAXA90055MQQ/000002_1478318093.jpg',
          price: 64
        },
        {
          name: '來一客_韓式泡菜風味',
          img: 'https://e.ecimg.tw/items/DBAAAXA90055MMJ/000002_1476842761.jpg',
          price: 60
        },
        {
          name: '來一客_鮮蝦魚板風味',
          img: 'https://f.ecimg.tw/items/DBAAAXA90055MM9/000002_1478318085.jpg',
          price: 62
        },
        {
          name: '來一客_肉燥菠菜風味',
          img: 'https://c.ecimg.tw/items/DBAAAXA90055NJK/000002_1476842632.jpg',
          price: 66
        }
      ]
    }
  },
  methods: {
    addCart (item) {
      this.$store.commit('addCart', item)
    }
  }
}
</script>
