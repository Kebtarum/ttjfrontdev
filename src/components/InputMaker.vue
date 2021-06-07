<template>
    
        <div class="form__item" >
            <label class="form__item-label">{{input.label}}</label>
            
            <input class="form__item-input"
            :type = "input.type"
            :name = "input.name"
            :placeholder= "input.placeholder"

            :value='modelValue'
            @input= '$emit("update:modelValue", $event.target.value)' 
            >
        </div>
        
    
</template>

<script>
// import {validationMixin} from 'vuelidate'

export default {
    name: 'InputMaker',
    props: {
        modelValue: [String, Number, Boolean],
        input: Object,
    },
  
}
</script>

<style scoped lang="scss">
// .add-form{
//     margin-bottom: 40px;
// }
// .form-control{
//     margin: 20px 0;
//     label{
//         display: block;
//     }
//     input{
//         outline: none;
//         border: none;
//         border-bottom: 1px solid #ddd;
//         font-size: 1em;
//         padding: 5px 0;
//         margin: 10px 0 5px 0;
//         width: 100%;
//     }
// }
// .form-control-check{
//     display: flex;
//     align-items: center;
//     justify-content: space-between;
//     label{
//         flex: 2;
//     }
//     input{
//         flex: 1;
//         height: 20px;
//     }
// }


</style>