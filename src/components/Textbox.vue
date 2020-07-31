<template>
  <div class="editable">
     <div v-if="!editing">
      <span class='text' @click="enableEditing">{{value}}</span>
    </div>
    <div v-if="editing">
        <input v-model="tempValue" @keyup="inputData" class="input"/>
        <a @click="saveEdit" class="custome-btn"> 
          <img src="https://f0.pngfuel.com/png/811/919/check-icon-png-clip-art.png">
        </a>
        <a @click="disableEditing" class="custome-btn"> 
            <img src="https://f0.pngfuel.com/png/776/857/check-mark-international-red-cross-and-red-crescent-movement-american-red-cross-red-cross-mark-round-red-x-logo-png-clip-art.png">
        </a>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
        value: 'Please enter value',
        tempValue: null,
        editing: false,
    }
  },
  props:{
    inputValue: {
      default:"Please enter value"
    }
  },
  watch:{
    inputValue: (val) =>{
      this.value = val
    },
  },
  methods: {
    enableEditing(){
      this.tempValue = this.value;
      this.editing = true;
    },
    disableEditing(){
      this.tempValue = null;
      this.editing = false;
    },
    inputData(e){
      this.$emit('input',this.tempValue)
      if(e.keyCode==13){
        this.saveEdit()
      }
    },
    saveEdit(){
      this.value = this.tempValue;
      this.disableEditing();
      this.$emit('save',this.value)
    }
  }
}
</script>
<style>
.editable span.text:hover {
    border-bottom: 2px dotted;
}
.editable input {
    vertical-align: top;
    border: 0;
    border-bottom: black 2px dotted;
    width: auto;
    min-width: 50px;
}
.editable input.input:focus {
    outline: none;
}
.editable .custome-btn {
    width: 20px;
    height: 20px;
    margin-left: 5px;
    cursor: pointer;
}
.editable .custome-btn img{
    width: 20px;
}
</style>