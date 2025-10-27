<template>
    <div class="nominations-filter">
        <select name="category" v-model="category">
            <option v-for="item in categoryList" :key="item" :value="item">{{ item }}</option>
        </select>
        <select name="nomination" v-model="nomination" v-if="category !== ''">
            <option v-for="item in nominationsList" :key="item" :value="item">{{ item }}</option>
        </select>
    </div>
</template>

<script setup >

const props = defineProps({
    categoryList: {
        type: Array,
        required: true
    },
    nominationsList: {
        type: Array,
        required: true
    }
})

const category = defineModel("category", {
    type: [String, Number, Boolean],
    required: true,
    default: ''
})

const nomination = defineModel("nomination", {
    type: [String, Number, Boolean],
    required: true,
    default: ''
})

</script>

<style lang="sass">
.paw-btn
  display: inline-flex
  align-items: center
  justify-content: center
  width: 40px
  height: 40px
  font-size: 30px
  border: none
  border-radius: 8px

  background: transparent
  color: transparent      
  opacity: 0              
  transition: opacity .2s ease, background-color .2s ease, color .2s ease

.dynamic-template_paw .paw-btn
    &::after
        content: ''
    &:hover, &:focus-visible
        opacity: 1
        background: inherit      
        color: #fff            
    &:hover::after, &:focus-visible::after
        content: ''

.dynamic-template_paw
        cursor: zoom-in

.nominations-filter
    margin-top: 40px
    display: flex
    gap: 20px
    & select
        display: block
        padding: 10px 15px
    & option
        padding: 10px 15px

</style>