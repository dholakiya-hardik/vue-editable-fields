<template>
  <div class="editable" :class="classes">
     <div v-if="!editing">
      <span class='text' @click="enableEditing">{{value}}</span>
    </div>
    <div v-if="editing">
        <textarea class="form-control" v-if="isMultiLine" v-model="tempValue" @keyup="inputData" required></textarea>
        <input v-model="tempValue" @keyup="inputData" class="form-control" :type="isNumeric?'number':'text'" @keypress="isNumber($event)" placeholder="Please enter value" required v-else/>
        <a @click="saveEdit" class="custome-btn save">&#10003;</a>
        <a @click="disableEditing" class="custome-btn remove">&#10006;</a>
    </div>
  </div>
</template>
<script>
export default {
  name:"Textbox",
  data () {
    return {
        value: this.inputValue,
        tempValue: null,
        editing: false,
    }
  },
  props:{
    inputValue: {
      default:null
    },
    classes: {
        type:[String,Array],
        default:null  
    },
    isMultiLine:{
      type:Boolean,
      default:false
    },
    isNumeric:{
      type:Boolean,
      default:false
    }
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
    isNumber: function(e) {
      e = (e) ? e : window.event;
      var charCode = (e.which) ? e.which : e.keyCode;
      if (this.isNumeric==true && (charCode > 31 && (charCode < 48 || charCode > 57)) && charCode !== 46) {
        e.preventDefault();
      } else {
        return true;
      }
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
    font-size: 22px;
    cursor: pointer;
}
.editable .custome-btn img{
    width: 20px;
}
.save{
    color: #2196F3;
    font-weight: 900;
}
.remove {
  color: #f32121;
}
</style>