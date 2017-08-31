<template>
  <div class="text-center" id="app">
    <div>
    <h1 id="titre">Traducteur</h1>
    <tradform v-on:formSubmit="tradtext"></tradform>
    <tradout v-text="texttrad"></tradout>
    </div>
  </div>
</template>

<script>
import tradform from './components/tradform'
import tradout from './components/tradout';

export default {
  name: 'app',
  components:{
    tradform,
    tradout
  },
  data :function(){
    return {
      texttrad:''
    }
  },
  methods: {
    tradtext:function(text, language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170329T180255Z.3c18d2dc7b65d525.f23ed9a9efa992bded4ef96334e3c154f61d2dea&lang=fr-'+language+'&text='+text)
      .then((response) => {
        this.texttrad =response.body.text[0];
  });
    }
  }
}
</script>

<style>
#app {
display: flex;
justify-content: center;
align-items: center;
height: 100vh;
}

#titre {
  color: #BEF574;
}
</style>
