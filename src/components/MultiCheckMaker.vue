<template>
    
        <div class="form__item">
            <label class="form__item-label">{{input.label}}</label>
            <div class="">
                <label :key="value.id"  v-for="value in values" >

                <input 
                type = "checkbox"
                :name = "input.name"

                :value='value'
                :checked="modelValue.includes(value)"
                @change='evnt => onChange(evnt.target.value)'
                >
                <!-- @change= '$emit("update:modelValue", $event.target. value)' -->
                {{value}}
                </label>
            </div>
            
            
        </div>
    
</template>

<script>
// import {validationMixin} from 'vuelidate'

export default {
    name: 'MultiCheckMaker',
    props: {
        input: Object,
        modelValue: Array,
        values: Array,
        wtf: Boolean,
    },
    methods:{

        onChange(value) {
            if(this.modelValue.includes(value)){
                this.$emit('update:modelValue', this.modelValue.filter((cv)=> cv !== value))
            }
            else{
                this.$emit('update:modelValue', this.modelValue.concat(value))
            }
        }
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