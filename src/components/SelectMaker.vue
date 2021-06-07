<template>
    
        <div class="form__item" >
            <label class="form__item-label">{{input.label}}</label>
            <select class="form__item-input" :name = "input.name" 
            :value='modelValue'
            @input= '$emit("update:modelValue", $event.target.value)' >
                <option :key="value.id" v-for="value in values" :value="value">{{value}}</option>
            </select>
            
        </div>
        
</template>

<script>
// import {validationMixin} from 'vuelidate'

export default {
    name: 'SelectMaker',
    props: {
        modelValue: [String, Number, Boolean],
        input: Object,
        values: Array,
        wtf: Boolean,
    },
  
}
</script>

<style scoped lang="scss">

</style>