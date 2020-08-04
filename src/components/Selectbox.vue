<template>
  <div class="editable" :class="classes">
     <div v-if="!editing">
      <span class='text' @click="enableEditing">{{value}}</span>
    </div>
    <div v-if="editing">
        <select v-model="tempValue">
            <option v-if="showDefaultOption" value="">{{defaultOptionLabel}}</option>
            <!-- eslint-disable vue/no-use-v-if-with-v-for,vue/no-confusing-v-for-v-if -->
            <option v-for="(val, index) in options" :key="index" :value="val.value" @click="selectOption" v-if="typeof val=='object'">{{val.label}}</option>
            <option v-for="(val, index) in options" :key="index" :value="val" @click="selectOption" v-if="typeof val=='string'">{{val}}</option>
        </select>
        <a @click="saveEdit" class="custome-btn save">&#10003;</a>
        <a @click="disableEditing" class="custome-btn remove">&#10006;</a>
    </div>
  </div>
</template>
<script>
export default {
  name:"Selectbox",
  data () {
    return {
        value: this.selectedOption,
        tempValue: null,
        editing: false,
    }
  },
  props:{
    selectedOption: {
      type: String,
      default:null
    },
    options:{
        type:Array
    },
    showDefaultOption:{
        type: Boolean,
        default:true
    },
    classes: {
        type:[String,Array],
        default:null  
    },
    defaultOptionLabel:{
        type: String,
        default:"Please Select"  
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
    selectOption(){
      this.$emit('selectOption', this.tempValue)
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
.editable select {
    vertical-align: top;
    border: 0;
    border-bottom: black 2px dotted;
    width: auto;
    min-width: 50px;
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