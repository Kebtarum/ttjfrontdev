<template>
    <div @dblclick="$emit('toggle-reminder', item.id)" class="client-list__item">
        <div class="client-list__info">
            <h3 class="client-list__item-title">{{ item.lastName }} {{ item.firstName }} {{ item.middleName }}
             <!-- <i @click="$emit('delete-item', item.id)" class="fas fa-times"></i> -->
            </h3>
            <div class="client-list__info-row"><span>Фамилия:</span><span>{{ item.lastName }}</span></div> 
            <div class="client-list__info-row"><span>Имя:</span> <span>{{ item.firstName }}</span></div>
            <div class="client-list__info-row"><span>Отчество:</span> <span>{{ item.middleName }}</span></div>
            <div class="client-list__info-row"><span>День рождения:</span> <span>{{ item.birthday }}</span></div>
            <div class="client-list__info-row"><span>Номер телефона:</span> <span>{{ item.phoneNumber }}</span></div>
            <div class="client-list__info-row"><span>Пол:</span>  <span>{{ item.sex }}</span></div>
            <div class="client-list__info-row"><span>Группа клиентов:</span><span><p :key="client.id" v-for="client in item.clientGroup">{{ client }}</p></span></div>
            <div class="client-list__info-row"><span>Лечащий врач:</span><span>{{ item.doctor }}</span></div>
            <div class="client-list__info-row"><span>Не отправлять СМС:</span><span>{{ buf = item.getLetter ? buf = 'Не отправлять': buf = 'Отправлять' }}</span></div>
            <h4 class="client-list__info-title">
                Адрес
            </h4>
            <div class="client-list__info-row"><span>Индекс:</span><span>{{ item.adress.zipCode }}</span></div>
            <div class="client-list__info-row"><span>Страна:</span><span>{{ item.adress.country }}</span></div>
            <div class="client-list__info-row"><span>Область:</span><span>{{ item.adress.region }}</span></div>
            <div class="client-list__info-row"><span>Город:</span><span>{{ item.adress.city }}</span></div>
            <div class="client-list__info-row"><span>Улица:</span><span>{{ item.adress.street }}</span> </div>
            <div class="client-list__info-row"><span>Дом:</span><span>{{ item.adress.house }}</span> </div>
            <h4 class="client-list__info-title">
                Паспорт
            </h4>
            <div class="client-list__info-row"><span>Тип документа:</span><span>{{ item.passport.documentType }}</span> </div>
            <div class="client-list__info-row"><span>Серия:</span><span>{{ item.passport.series }}</span> </div>
            <div class="client-list__info-row"><span>Номер:</span><span>{{ item.passport.number }}</span> </div>
            <div class="client-list__info-row"><span>Кем выдан:</span><span>{{ item.passport.issuedBy }}</span> </div>
            <div class="client-list__info-row"><span>Дата выдачи:</span><span>{{ item.passport.dateOfIssue }}</span> </div>
            
        </div>
        <button @click="$emit('delete-item', item.id)" class="close">
            <img src="../assets/close.svg" alt="close">
        </button>
    </div>
</template>

<script>
export default {
    name: 'Item',
    props: {
        item: Object
    },
}
</script>

<style scoped lang="scss">

</style>