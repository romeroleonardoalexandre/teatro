
<template>
  <div id="app">
		<div class="container center-block" align="center">
			<div class="row" v-for="line in lines">
				<seat v-for="col in cols"></seat>
			</div>
      <button class="btn btn-info"@click="createPDF()">PDF</button>
		</div>
	  
  </div>
</template>

<script>
import seat from './component/seat';
import jsPDF from 'jspdf'

export default {
components: { seat },
  name: 'app',
  data () {
    return {
      lines:3,
			cols:6,
    }
  },
  methods: {
    createPDF () {
      
      var specialElementHandlers = {
      'container': function(element, renderer){
       return true;
    }
    };
      var doc = new jsPDF();
     
      doc.fromHTML(document.body.innerHTML, 15, 15, {
	      'width': 170, 
	      'elementHandlers': specialElementHandlers
        },function(bla) {   doc.save('teste.pdf');
      });
    }
  }

}
</script>

<style lang="scss">
body{
  background-image: url("./assets/background1.jpg")
}
@import '../node_modules/bootstrap/scss/bootstrap.scss';
</style>
