<template>
  <div>
      <input placeholder="Date" v-model="date">
      <input placeholder="Categoru" v-model="categoru">
      <input placeholder="Price" v-model.number="price">
      <button @click="save">Save</button>
  </div>
</template>

<script>
export default {
data() {
    return {
        date:"",
        categoru: "",
        price:0
    }
},
methods: {
    save(){
        const {date, categoru, price} = this
        this.$emit("add",{date,categoru,price})
    }
},
}
</script>

<style>

</style>