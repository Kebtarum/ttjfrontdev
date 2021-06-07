<template>
  <div class="container">
    <FormComp @add-item="addItem" />
    <div class="client-list">
      <List @toggle-reminder="toggleReminder" @delete-item="deleteItem" :list="list" />
    </div>
  </div>
</template>

<script>
import FormComp from './components/FormComp'
import List from './components/List'

export default {
  name: 'App',
  components: {
    FormComp,
    List,
  },
  data(){
    return{
      list: [],
    }
  },
  methods: {
    addItem(item){
      this.list = [...this.list, item]
    },
    deleteItem(id){
      if(confirm('Are you sure?')){
        this.list = this.list.filter((item)=>item.id !== id)
      }
    },
  },
  created(){
    this.list = [
      {
        id: 1,
        text: 'Food Shopping',
        day: 'March 3rd at 11:00am',
        reminder: false,
        lastName: 'Петров',
        firstName: 'Петя',
        middleName: 'Петрович',
        birthday: '20.20.2020',
        phoneNumber: '79054443322',
        sex: 'М',
        clientGroup: ['VIP'],
        doctor: 'Захаров',
        getLetter: false,
        adress: {
          zipCode: '109129',
          country: 'Россия',
          region: 'Ленинградская область',
          city: 'Санкт-Петербург',
          street: 'ПетраВеликого',
          house: 'П20',
        },
        passport: {
          documentType: 'Паспорт',
          series: 'N3',
          number: '123123123',
          issuedBy: 'Петрова',
          dateOfIssue: '10.10.1010',
        },

      },
    ]
  }
}
</script>

