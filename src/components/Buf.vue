<template>
    <form @submit="onSubmit" class="add-form">
        <!-- <InputMaker v-model = "text" :input="{ label: 'Test', name: 'text', type: 'text', placeholder: 'Add Task' }" />
        <InputMaker v-model = "day" :input="{ label: 'Day & Time', name: 'day', type: 'text', placeholder: 'Add Day & Tiem' }" />
        <InputMaker v-model = "reminder" :input="{ label: 'Set reminder', name: 'reminder', type: 'checkbox' }" /> -->

        <InputMaker v-model = "lastName" :input="{ label: 'Фамилия', name: 'lastName', type: 'text', placeholder: 'Введите фамилию' }" />
        <InputMaker v-model = "firstName" :input="{ label: 'Имя', name: 'firstName', type: 'text', placeholder: 'Введите имя' }" />
        <!-- <span v-if="v$.firstName.$error">
            {{v$.firstName.$errors[0].$message}}
        </span> -->
        <InputMaker v-model = "middleName" :input="{ label: 'Отчество', name: 'middleName', type: 'text', placeholder: 'Введите отчество' }" />
        <InputMaker v-model = "birthday" :input="{ label: 'Дата рождения', name: 'birthday', type: 'text', placeholder: 'Your birthday' }" />
        <InputMaker v-model = "phoneNumber" :input="{ label: 'Номер телефона', name: 'phoneNumber', type: 'text', placeholder: 'Введите номер телефона' }" />
<!-- sex -->
        <RadioMaker v-model = "sex" :values="['М', 'Ж']" :input="{ label: 'Пол', name: 'sex', type: 'radio' }" />

<!--  multi-select      -->
        <MultiCheckMaker v-model = "clientGroup" :values="['VIP', 'Проблемные', 'ОМС']" :input="{ label: 'Группа клиентов', name: 'clientGroup'}" />
<!-- select -->
        <SelectMaker v-model = "doctor" :values="['Иванов', 'Захаров', 'Чернышева']" :input="{ label: 'Лечащй врач', name: 'doctor'}" />

        <!-- <InputMaker v-model = "getLetter" :input="{ label: 'Get Letter', name: 'getLetter', type: 'checkbox' }" /> -->

        <div class="form-control form-control-check">
            <label>Не отправлять СМС</label>
            <input type="checkbox" v-model="getLetter" name="getLetter" >
        </div>

        <h4 class="form__title">Адрес</h4>
        <InputMaker v-model = "zipCode" :input="{ label: 'Номер телефона', name: 'zipCode', type: 'text', placeholder: 'Введите индекс' }" />
        <InputMaker v-model = "country" :input="{ label: 'Страна', name: 'country', type: 'text', placeholder: 'Введите страну' }" />
        <InputMaker v-model = "region" :input="{ label: 'Область', name: 'region', type: 'text', placeholder: 'Введите область' }" />
        <InputMaker v-model = "city" :input="{ label: 'Город', name: 'city', type: 'text', placeholder: 'Введите город' }" />
        <InputMaker v-model = "street" :input="{ label: 'Улица', name: 'street', type: 'text', placeholder: 'Введите улицу' }" />
        <InputMaker v-model = "house" :input="{ label: 'Дом', name: 'house', type: 'text', placeholder: 'Введите дом' }" />
        
        <h4 class="form__title">Паспорт</h4>
        <SelectMaker v-model = "documentType" :values="['Паспорт', 'Свидетельство о рождении', 'Вод. удостоверение']" :input="{ label: 'Тип документа', name: 'documentType'}" />
        <InputMaker v-model = "series" :input="{ label: 'Серия', name: 'series', type: 'text', placeholder: 'Введите серию' }" />
        <InputMaker v-model = "number" :input="{ label: 'Номер', name: 'number', type: 'text', placeholder: 'Введите номер' }" />
        <InputMaker v-model = "issuedBy" :input="{ label: 'Кем выдан', name: 'issuedBy', type: 'text', placeholder: 'Кем выдан' }" />
        <InputMaker v-model = "dateOfIssue" :input="{ label: 'Дата выдачи', name: 'dateOfIssue', type: 'text', placeholder: 'Дата выдачи' }" />


    
            
        <input type="submit" name="Save Task" class="btn btn-block" >
    </form>
</template>

<script>

import useValidate from '@vuelidate/core'
import { required } from '@vuelidate/validators';
import { reactive, computed} from 'vue';

import InputMaker from './InputMaker';
import RadioMaker from './RadioMaker';
import SelectMaker from './SelectMaker';
import MultiCheckMaker from './MultiCheckMaker';

export default {
    name: 'FormComp',
    // mixins: [ validationMixin ],
    components: {
        InputMaker,
        RadioMaker,
        SelectMaker,
        MultiCheckMaker,
    },
    setup(){
        const state = reactive({
            id: "",
            lastName: "Петров",
            firstName: "Петя",
            middleName: "Петрович",
            birthday: "02.02.1992",
            phoneNumber: "76665554433",
            sex: "М",
            clientGroup: ['VIP'],
            doctor: "Захаров",
            getLetter: true,
            adress: {
                zipCode: "101202",
                country: "РФ",
                region: "Ленинградская область",
                city: "СПБ",
                street: "Петровский",
                house: "Петрова",
            },
            passport: {
                documentType: "Паспорт",
                series: "P",
                number: "1234567890",
                issuedBy: "Петровава",
                dateOfIssue: "20.20.2020",
            }, 
        })

        const rules = computed (()=>{
            return{
                lastName: {required},
            firstName: {required},
            birthday: {required},
            phoneNumber: {required},
            clientGroup: {required},
            adress: {
                city: {required},
            },
            passport: {
                documentType: {required},
                dateOfIssue: {required},
            }
            }
        })

        const v$ = useValidate(rules, state)

        return{
            state,
            v$
        }
    },
    // data(){
    //     return{
    //         v$: useValidate(),
    //         id: "",
    //         lastName: "Петров",
    //         firstName: "Петя",
    //         middleName: "Петрович",
    //         birthday: "02.02.1992",
    //         phoneNumber: "76665554433",
    //         sex: "М",
    //         clientGroup: ['VIP'],
    //         doctor: "Захаров",
    //         getLetter: true,
    //         adress: {
    //             zipCode: "101202",
    //             country: "РФ",
    //             region: "Ленинградская область",
    //             city: "СПБ",
    //             street: "Петровский",
    //             house: "Петрова",
    //         },
    //         passport: {
    //             documentType: "Паспорт",
    //             series: "P",
    //             number: "1234567890",
    //             issuedBy: "Петровава",
    //             dateOfIssue: "20.20.2020",
    //         },
    //     }
    // },
    // validations() {
    //     return {
    //         lastName: {required},
    //         firstName: {required},
    //         birthday: {required},
    //         phoneNumber: {required},
    //         clientGroup: {required},
    //         adress: {
    //             city: {required},
    //         },
    //         passport: {
    //             documentType: {required},
    //             dateOfIssue: {required},
    //         }
    //     }
    // },
    methods: {
        onSubmit(e){
            console.log(this.v$)
            e.preventDefault()
            // debugger
            // if(!this.firstName){
            //     console.log(this.text)
            //     alert('Please add a task')
            //     return
            // }
            this.v$.$validate()
            if(!this.v$.$error){
                alert('Добавили')
                    const newTask = {
                    id: Math.floor(Math.random()* 10000),

                    lastName: this.lastName,
                    firstName: this.firstName,
                    middleName: this.middleName,
                    birthday: this.birthday,
                    mobilePhone: this.mobilePhone,
                    sex: this.sex,
                    clientGroup: this.clientGroup,
                    doctor: this.doctor,
                    getLetter: this.getLetter,
                    adress: {
                        zipCode: this.adress.zipCode,
                        country: this.adress.country,
                        region: this.adress.region,
                        city: this.adress.city,
                        street: this.adress.street,
                        house: this.adress.house,
                    },
                    passport: {
                        documentType: this.passport.documentType,
                        series: this.passport.series,
                        number: this.passport.number,
                        issuedBy: this.passport.issuedBy,
                        dateOfIssue: this.passport.dateOfIssue,
                    },
                }
            
                this.$emit('add-task', newTask)


                this.lastName = "";
                this.firstName = "";
                this.middleName = "";
                this.birthday = "";
                this.phoneNumber = "";
                this.sex = "";
                this.clientGroup = [];
                this.doctor = "";
                this.getLetter = false;
            }
            else {
                alert('НЕ ПРОШЕЛ ВАЛИДАЦИЮ')
            }
        }

            
    }
    // props: {
    //     task: Object
    // },
}
</script>

<style scoped lang="scss">
.add-form{
    margin-bottom: 40px;
}
.form-control{
    margin: 20px 0;
    label{
        display: block;
    }
    input {
        outline: none;
        border: none;
        border-bottom: 1px solid #ddd;
        font-size: 1em;
        padding: 5px 0;
        margin: 10px 0 5px 0;
        width: 100%;
    }
}
.form-control-check{
    display: flex;
    align-items: center;
    justify-content: space-between;
    label{
        flex: 2;
    }
    input{
        flex: 1;
        
    }
}
</style>