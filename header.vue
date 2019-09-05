<!-- navBar -->
<template>
  <v-card class="header-cpnt" dark flat tile :color="bgc">
    <v-layout align-center>
      <v-flex @click="doSth" xs3>
        <i class="xiyu  iconleft"></i>
      </v-flex>
      <v-flex xs6 class="text-center title">
				<!-- 针对中部复杂化的情况，使用slot则不使用props中的text -->
				<slot name="center"></slot>
				{{text}}
			</v-flex>
      <v-flex class="subtitle-2 text-center v-rating"  @click="edit" xs3>{{rightText}}</v-flex>
    </v-layout>
  </v-card>
</template>

<script>
export default {
  props:{
    text:{
      type: String,
      default(){
        return ''
      }
    },
    rightText:{
      type: String,
      default(){
        return ''
      }
    },
    bgc:{
      type: String,
      default(){
        return '#2196F3'
      }
    },
    hideRef:{
      type: Boolean,
      default(){
        return false
      }
    }
  },
  methods: {
    doSth(){
      this.$emit('doSomething')
    },
    edit(){
      if(!this.rightText){
        return
      }
      this.$emit('edit')
    }
  }
}

</script>
<style lang='scss' scoped>
  .header-cpnt{
    z-index: 999;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    >div{
      height: 45px;
      box-sizing: border-box;
    }
   .xiyu{
     font-size: 30px;
   }
  }
</style>