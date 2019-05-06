<template>
  <q-page class="flex flex-center flex-column">
    <button @click="get">GET</button>
    <div v-html="text"></div>
  </q-page>
</template>

<style>
</style>

<script>
export default {
  name: 'PageIndex',
  data() {
    return {
      text: null,
    }
  },

  methods: {
    get() {



      window.t = this;
      this.$axios.get('https://cors-anywhere.herokuapp.com/https://mpeisport.ru/schedule')
      .then(e=>{
        const div = document.createElement('div')
        div.innerHTML = e.data;
        window.div= div;

        this.text = div.querySelectorAll('.table-responsive')[0].innerHTML



        arr = [];

div.querySelectorAll('tbody tr').forEach( tr =>{
	const ret = {sections: [] };
	tr.querySelectorAll('td').forEach((td,i) => {
		if(i==0) ret.time = td.innerText
		else ret.sections.push(td.innerText)
	})
	arr.push(ret)
})

// на 14:40 не пашет
window.addEventListener('storage', e =>console.log(e.key));
window.localStorage.setItem('s22s',123)



      })
      .catch(e=>this.text = e)
    }
  }

}
</script>
