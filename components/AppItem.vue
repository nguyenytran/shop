<template>
  <div class="item">
    <p>{{ item.name }}</p>
    <span v-if="item.sale" class="salepill">Sale</span>
    <img :src="`img/${item.img}`" :alt="`Image of ${item.name}`" />
    <p>{{ item.price | usdollar }}</p>
    <button class="add" @click="addItem">
      Add Item
    </button>
  </div>
</template>

<script>
export default {
  filters: {
    usdollar: function(value) {
      return `$${value}`
    }
  },
  props: {
    item: {
      type: Object,
      required: true
    },
    index: {
      type: Number,
      required: true
    }
  },
  methods: {
    addItem() {
      this.$store.commit("addItem", this.item)
    }
  }
}
</script>

<style scoped lang="scss">
.item {
  border-radius: 5px;
  padding: 20px;
  background: white;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: relative;
}

.salepill {
  background: rgb(232, 35, 25);
  color: white;
  font-family: "Barlow", sans-serif;
  position: absolute;
  right: 30px;
  top: 60px;
  padding: 2px 10px 4px;
  text-transform: uppercase;
  font-size: 13px;
  font-weight: 700;
  border-radius: 1000px;
}

p {
  font-size: 18px;
}
</style>
