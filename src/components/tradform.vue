<template>
  <div class="text-center"id="tradform">
  <form v-on:submit="formSubmit">
    <input type="text" v-model="texttrad" placeholder="Entrer un mot...">
      <select v-model="language">
        <option value="ru">Russe</option>
        <option value="es">Espagnol</option>
        <option value="en">Anglais</option>
        <option value="zh">Chinois</option>

      </select>
    <input type="submit" value="trad">
  </form>

  </div>
</template>

<script>

export default {
  name: 'tradform',
  data() {
    return {
      texttrad:'',
      language:'en'
    }
  },
  methods: {
    formSubmit(e) {
      this.$emit('formSubmit', this.texttrad, this.language);
      e.preventDefault();
    }
  }
}
</script>

<style>

</style>
