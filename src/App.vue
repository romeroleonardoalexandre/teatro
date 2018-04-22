
<template>
  <div id="app">
		<div class="container">
			<div class="row" v-for="line in lines">
				<seat v-for="col in cols"></seat>
			</div>
		</div>
	  
  </div>
</template>

<script>
import seat from './component/seat';

export default {
components: { seat },
  name: 'app',
  data () {
    return {
      lines:3,
			cols:6,
    }
  }

}
</script>

<style lang="scss">
@import '../node_modules/bootstrap/scss/bootstrap.scss';
</style>
