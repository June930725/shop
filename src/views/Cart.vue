<template lang="pug">
  #cart
    //- 清單陳列
    //- ul
    //-   li(v-for="(item, index) in items" :key="index") {{ item.name }}
    //- 表格陳列
    b-table(:items="items" :fields="fields" striped hover)
      template(#cell(action)="data")
        b-button(variant="danger" @click="del(data.index)")
          font-awesome-icon(:icon="['far', 'trash-alt']")
</template>

<script>
export default {
  name: 'Cart',
  data () {
    return {
      fields: [
        {
          key: 'name',
          lable: '商品名稱'
        },
        {
          key: 'price',
          lable: '價格'
        },
        {
          key: 'action',
          lable: '操作'
        }
      ]
    }
  },
  computed: {
    items () {
      // 直接取 vuex 的 items
      // return this.$store.state.items
      // 呼叫 vuex 的 getters
      return this.$store.getters.items
    }
  },
  methods: {
    del (index) {
      this.$store.commit('delCart', index)
    }
  }
}
</script>
