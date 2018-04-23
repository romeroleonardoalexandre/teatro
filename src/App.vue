
<template>
  <div id="app">
		<div class="container">
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
      // let pdfName = 'test'; 
      var specialElementHandlers = {
      'container': function(element, renderer){
       return true;
    }
    };
      var doc = new jsPDF();
      // doc.text("Hello World", 10, 10);
      // doc.save(pdfName + '.pdf');
      doc.fromHTML(document.body.innerHTML, 15, 15, {
	      'width': 170, 
	      'elementHandlers': specialElementHandlers
        },function(bla) {   doc.save('saveInCallback.pdf');
      });
    }
  }

}
</script>

<style lang="scss">
@import '../node_modules/bootstrap/scss/bootstrap.scss';
</style>
