
<template>
    <div class="col-lg-1 text-center" :style="{ backgroundColor: this.currentSeat.color, opacity:0.7}" @click="change()">
        <img src="../assets/seat.png" style="width:100%;height:80%;">
        <p>{{this.currentSeat.desc}}</p>
    </div>
</template>

<script>
export default {
    props:['positions'],
    name: 'seat',
    data () {
        return {
            seat:[
                { 
                    id:0,
                    desc:"Disponivel",
                    color:""
                },
                { 
                    id:1,
                    desc:"Ocupado",
                    color:"#c9c5c5"
                },
                { 
                    id:2,
                    desc:"Indisponivel",
                    color:"#d64806"
                },
            ],
        currentSeat:{},
        position:{
            x:0,
            y:0
        }
    }
  },
  mounted:function(){
      this.currentSeat = this.seat[0];
      this.position.x = this.positions[0];
      this.position.y = this.positions[1];
  },
	methods:{
		change:function(){
            if(this.currentSeat.id == 0){
                this.currentSeat = this.seat[1];
            }else if(this.currentSeat.id == 1){
                this.currentSeat = this.seat[0];
            }else{
                alert("Não esta disponivel");
            }
			
		}
	}
}
</script>
<style scoped>
p{
    font-size:10px;
}

</style>


