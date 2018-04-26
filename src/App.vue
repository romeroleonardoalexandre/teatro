
<template>
  <div id="app">
		<div class="container center-block" align="center">
      <div class="row">
        <div class="col-lg-1 text-right" style="right:12px"  v-for="(charr) in alphabet.slice(0, cols)"><h4>{{charr}}</h4></div>
      </div>
			<div class="row" v-for="(line, index) in lines">
        <h4 style="margin-top:20px;">{{index}}</h4>
				<seat v-for="(col, index2) in cols" :positions="[index,index2]"></seat>
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
      lines:8,
			cols:12,
      alphabet:["A","B","C","D", "E", "F", "G", "H", "I", "J", "K", "L", "M"]
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
