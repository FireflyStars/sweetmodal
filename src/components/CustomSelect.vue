<template>
  <div class="custom-select" :tabindex="tabindex" :class="open ? 'arrow-left' : 'arrow-down'" @blur="open = false">
    <div class="selected" :class="{open: open}" @click="open = !open">{{ selected }}</div>
    <div class="items" :class="{selectHide: !open}">
      <div
        class="item"
        v-for="(option, i) of options"
        :key="i"
        @click="selected=option; open=false; $emit('input', option)"
      >{{ option }}</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    options: {
      type: Array,
      required: true
    },
    tabindex: {
      type: Number,
      required: false,
      default: 0
    },
    placeholder:{
        type: String,
        required: true,
        default: ''
    }
  },
  data() {
    return {
      selected: this.options.length > 0 ? this.options[0] : this.placeholder,
      open: false
    };
  },
  mounted() {
      this.selected = this.placeholder;
    this.$emit("input", this.selected);
  }
};
</script>

<style scoped>
.custom-select {
  position: relative;
  width: 100%;
  text-align: left;
  cursor: pointer;
  font-size: 12px;
  font-weight: 600;
  color: #424242;
  outline: none;
  height: 33px;
  line-height: 33px;
  background-size: auto;  
  text-transform: capitalize;
}
.arrow-down{
background: url(../assets/down-arrow.png) no-repeat center right;  
}
.arrow-left{
background: url(../assets/left-arrow.png) no-repeat center right;  
}
.selected {
  border: none;
  border-bottom: 1px solid #000;
  color: #424242;
  cursor: pointer;
  user-select: none;
}

.selected:after {
  position: absolute;
  content: "";
  top: 22px;
  right: 10px;
  width: 0;
  height: 0;
  border: 4px solid transparent;
  border-color: #fff transparent transparent transparent;
}

.items {
  z-index: 1000;
  color: #424242;
  /* border: solid 1px #424242; */
  overflow: hidden;
  /* border-right: 1px solid #424242;
  border-left: 1px solid #424242; */
  position: absolute;
  background-color: white;
  left: 0;
  right: 0;
}

.item {
  color: black;
  font-weight: 400;
  padding-left: 8px;
  cursor: pointer;
  user-select: none;
}

.item:hover {
  background-color: rgba(0, 0, 0, 0.1);;
}

.selectHide {
  display: none;
}
</style>