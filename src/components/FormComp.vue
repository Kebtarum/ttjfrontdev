<template>
    <form @submit="onSubmit" class="form">
        <!-- <InputMaker v-model = "text" :input="{ label: 'Test', name: 'text', type: 'text', placeholder: 'Add Task' }" />
        <InputMaker v-model = "day" :input="{ label: 'Day & Time', name: 'day', type: 'text', placeholder: 'Add Day & Tiem' }" />
        <InputMaker v-model = "reminder" :input="{ label: 'Set reminder', name: 'reminder', type: 'checkbox' }" /> -->
        <div class="form__box form__box-require ">
            <InputMaker  v-model = "state.lastName" :input="{ label: 'Фамилия', name: 'state.lastName', type: 'text', placeholder: 'Введите фамилию' }" />
            <span v-if="v$.lastName.$error" class="form__error">
            {{v$.lastName.$errors[0].$message}}
            </span>
        </div>
        <div class="form__box form__box-require ">
            <InputMaker  v-model = "state.firstName" :input="{ label: 'Имя', name: 'state.firstName', type: 'text', placeholder: 'Введите имя' }" />
            <span v-if="v$.firstName.$error" class="form__error">
            {{v$.firstName.$errors[0].$message}}
            </span>
        </div>
        <div class="form__box">
            <InputMaker v-model = "state.middleName" :input="{ label: 'Отчество', name: 'state.middleName', type: 'text', placeholder: 'Введите отчество' }" />
        </div>
        <div class="form__box form__box-require  form__box-date">
            <div class="form__item">

            <!-- <InputMaker  v-model = "state.birthday" :input="{ label: 'Дата рождения', name: 'state.birthday', type: 'text', placeholder: 'Your birthday' }" /> -->
            <label class="form__item-label">День рождения</label>
            <input class="form__item-input" v-model="state.birthday" type="date"  name="state.birthday" min="1940-01-01" max="2021-12-31">
            <span v-if="v$.birthday.$error" class="form__error">
            {{v$.birthday.$errors[0].$message}}
            </span>
            </div>
        </div>

<!--  -->
            
<!--  -->


        <div class="form__box form__box-require ">
            <InputMaker  v-model = "state.phoneNumber" :input="{ label: 'Номер телефона', name: 'state.phoneNumber', type: 'text', placeholder: 'Введите номер телефона' }" />
            <span v-if="v$.phoneNumber.$error" class="form__error">
            {{v$.phoneNumber.$errors[0].$message}}
            </span>
        </div>
<!-- sex -->
        <div class="form__box">
            <RadioMaker v-model = "state.sex" :values="['М', 'Ж']" :input="{ label: 'Пол', name: 'state.sex', type: 'radio' }" />
        </div>
<!--  multi-select      -->
        <div class="form__box form__box-require ">
            <MultiCheckMaker  v-model = "state.clientGroup" :values="['VIP', 'Проблемные', 'ОМС']" :input="{ label: 'Группа клиентов', name: 'state.clientGroup'}" />
            <span v-if="v$.clientGroup.$error" class="form__error">
            {{v$.clientGroup.$errors[0].$message}}
            </span>
        </div>
<!-- select -->
        <div class="form__box">
            <SelectMaker v-model = "state.doctor" :values="['Иванов', 'Захаров', 'Чернышева']" :input="{ label: 'Лечащй врач', name: 'state.doctor'}" />
        </div>

        <!-- <InputMaker v-model = "getLetter" :input="{ label: 'Get Letter', name: 'getLetter', type: 'checkbox' }" /> -->

        <div class="form__box form__box-check">
            <label class="form__item-label" >Не отправлять СМС</label>
            <input class="form__item-check" type="checkbox" v-model="getLetter" name="state.getLetter" >
        </div>

        <h4 class="form__title">Адрес</h4>
        <div class="form__box">
            <InputMaker v-model = "state.adress.zipCode" :input="{ label: 'Номер телефона', name: 'state.adress.zipCode', type: 'text', placeholder: 'Введите индекс' }" />
        </div>
        <div class="form__box">
            <InputMaker v-model = "state.adress.country" :input="{ label: 'Страна', name: 'state.adress.country', type: 'text', placeholder: 'Введите страну' }" />
        </div>
        <div class="form__box">
            <InputMaker v-model = "state.adress.region" :input="{ label: 'Область', name: 'state.adress.region', type: 'text', placeholder: 'Введите область' }" />
        </div>
        <div class="form__box form__box-require ">
            <InputMaker  v-model = "state.adress.city" :input="{ label: 'Город', name: 'state.adress.city', type: 'text', placeholder: 'Введите город' }" />
            <span v-if="v$.adress.city.$error" class="form__error">
            {{v$.adress.city.$errors[0].$message}}
            </span>
        </div>
        <div class="form__box">
            <InputMaker v-model = "state.adress.street" :input="{ label: 'Улица', name: 'state.adress.street', type: 'text', placeholder: 'Введите улицу' }" />
        </div>
        <div class="form__box">
            <InputMaker v-model = "state.adress.house" :input="{ label: 'Дом', name: 'state.adress.house', type: 'text', placeholder: 'Введите дом' }" />
        </div>

        <h4 class="form__title">Паспорт</h4>
        <div class="form__box form__box-require ">
            <SelectMaker  v-model = "state.passport.documentType" :values="['Паспорт', 'Свидетельство о рождении', 'Вод. удостоверение']" :input="{ label: 'Тип документа', name: 'state.passport.documentType'}" />
            <span v-if="v$.passport.documentType.$error" class="form__error">
            {{v$.passport.documentType.$errors[0].$message}}
            </span>
        </div>
        <div class="form__box">
            <InputMaker v-model = "state.passport.series" :input="{ label: 'Серия', name: 'state.passport.series', type: 'text', placeholder: 'Введите серию' }" />
        </div>
        <div class="form__box">
            <InputMaker v-model = "state.passport.number" :input="{ label: 'Номер', name: 'state.passport.number', type: 'text', placeholder: 'Введите номер' }" />
        </div>
        <div class="form__box">
            <InputMaker v-model = "state.passport.issuedBy" :input="{ label: 'Кем выдан', name: 'state.passport.issuedBy', type: 'text', placeholder: 'Кем выдан' }" />
        </div>
        <div class="form__box form__box-require form__box-date">
            <!-- <InputMaker  v-model = "state.passport.dateOfIssue" :input="{ label: 'Дата выдачи', name: 'state.passport.dateOfIssue', type: 'text', placeholder: 'Дата выдачи' }" />
            <span v-if="v$.passport.dateOfIssue.$error" class="form__error">
            {{v$.passport.dateOfIssue.$errors[0].$message}}
            </span> -->
            
            <div class="form__item">
                <label class="form__item-label">Дата выдачи</label>
                <input class="form__item-input" v-model = "state.passport.dateOfIssue" type="date"  name="state.passport.dateOfIssue" min="1940-01-01" max="2021-12-31">
                <span v-if="v$.passport.dateOfIssue.$error" class="form__error">
                {{v$.passport.dateOfIssue.$errors[0].$message}}
                </span>
                </div>
        
        </div>


    
            
        <input type="submit" name="Save Item" class="btn form__btn" >
    </form>
</template>

<script>

import useValidate from '@vuelidate/core'
import { required, helpers, minLength, maxLength, numeric } from '@vuelidate/validators';
import { reactive, computed } from 'vue';

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
            sex: "Ж",
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

        const mustBeSeven = (value) => value[0].includes('7')
        const requiredCustom = helpers.withMessage('Поле обязательно для заполнения', required)
        const mustBe = helpers.withMessage('Номер должен начинаться с 7 и содержать 11 цифр', mustBeSeven)
        const testMin = helpers.withMessage('Номер должен начинаться с 7 и содержать 11 цифр', minLength(11))
        const testMax = helpers.withMessage('Номер должен начинаться с 7 и содержать 11 цифр', maxLength(11))
        const testNum = helpers.withMessage('Номер должен начинаться с 7 и содержать 11 цифр', numeric)
        
        // minLength, maxLength, numeric, alpha

        const rules = computed (()=>{
            return{
                lastName: {
                    requiredCustom,
                    },
                firstName: {
                    requiredCustom,
                    },
                birthday: {
                    requiredCustom,
                },
                phoneNumber: {
                    requiredCustom,
                    testNum,
                    mustBe,
                    testMin,
                    testMax,
                    
                },
                clientGroup: {
                    requiredCustom,
                },
                adress: {
                    city: {
                        requiredCustom,
                    },
                },
                passport: {
                    documentType: {
                        requiredCustom,
                    },
                    dateOfIssue: {
                        requiredCustom,
                    },
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
            console.log(typeof this.v$.firstName)
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
                    const newItem = {
                    id: Math.floor(Math.random()* 10000),

                    lastName: this.state.lastName,
                    firstName: this.state.firstName,
                    middleName: this.state.middleName,
                    birthday: this.state.birthday,
                    mobilePhone: this.state.mobilePhone,
                    sex: this.state.sex,
                    clientGroup: this.state.clientGroup,
                    doctor: this.state.doctor,
                    getLetter: this.state.getLetter,
                    adress: {
                        zipCode: this.state.adress.zipCode,
                        country: this.state.adress.country,
                        region: this.state.adress.region,
                        city: this.state.adress.city,
                        street: this.state.adress.street,
                        house: this.state.adress.house,
                    },
                    passport: {
                        documentType: this.state.passport.documentType,
                        series: this.state.passport.series,
                        number: this.state.passport.number,
                        issuedBy: this.state.passport.issuedBy,
                        dateOfIssue: this.state.passport.dateOfIssue,
                    },
                }
            
                this.$emit('add-item', newItem)


                this.state.lastName = "";
                this.state.firstName = "";
                this.state.middleName = "";
                this.state.birthday = "";
                this.state.phoneNumber = "";
                this.state.sex = "";
                this.state.clientGroup = [];
                this.state.doctor = "";
                this.state.getLetter = false;
                this.state.adress.zipCode = "";
                this.state.adress.country = "";
                this.state.adress.region = "";
                this.state.adress.city = "";
                this.state.adress.street = "";
                this.state.adress.house = "";
                this.state.passport.documentType = "";
                this.state.passport.series = "";
                this.state.passport.number = "";
                this.state.passport.issuedBy = "";
                this.state.passport.dateOfIssue = "";

                this.v$.$reset()
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
</style>