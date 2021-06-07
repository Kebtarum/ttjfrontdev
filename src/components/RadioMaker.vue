<template>
    
        <div class="form__item" >
            <label class="form__item-label">{{input.label}}</label>
            <div class="radio-box">
                <label class="radio-box__label" :key="value.id"  v-for="value in values" >

                <input class="radio-box__input"
                type = "radio"
                :name = "input.name"

                :value='value'
                @change= '$emit("update:modelValue", $event.target. value)'
                :checked="value===modelValue"
                >
                {{value}}
                </label>
            </div>
            
            
        </div>
    
</template>

<script>
// import {validationMixin} from 'vuelidate'

export default {
    name: 'RadioMaker',
    props: {
        modelValue: [String, Number, Boolean],
        input: Object,
        values: Array,
        wtf: Boolean,
    },
  
}
</script>

<style scoped lang="scss">
// .form-control{
//     margin: 20px 0;
    
// }

// .form-control-radio{
//     display: flex;
//     align-items: center;
//     padding: 15px 0;
//     input{
//         margin-right: 3px;
//     }
// }
// .radio-label{
//     margin-right: 15px;
// }
</style>