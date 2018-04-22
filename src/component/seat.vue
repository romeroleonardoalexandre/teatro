
<template>
    <div class="col-md-2 text-center" :style="{ backgroundColor: this.currentSeat.color}" @click="change()">
        <img src="../assets/seat.png" style="width:100%;height:80%;">
        <h5>{{this.currentSeat.desc}}</h5>
    </div>
</template>

<script>
export default {
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
        currentSeat:{}
    }
  },
  created:function(){
      this.currentSeat = this.seat[0]
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

