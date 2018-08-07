<template>

  <div id="appy" class="checkForm">
    <h3>організація</h3>
    <input id="input9" class="orgLabel" v-model="orgLabel"/>

    <h3>рахунок від</h3>
    <input id="input0" v-model="fromDate"/>

    <h3>теперішній місяць</h3>
    <input id="input1" v-model="currentMounth"/>

    <h3>наступний місяць</h3>
    <input id="input2" v-model="nextMounth"/>

    <h3>комуналка</h3>
    <div class="divFlex">
      <div>
        <label for="input3">{{nomerRahunku}}</label>
        <input id="input3"v-model="utilityBill"/>
      </div>
      <div>
        <label for="input4">{{summa}}</label>
        <input id="input4"v-model="utilityBillSumm"/>
      </div>
    </div>

    <h3>земля</h3>
    <div class="divFlex">
      <div>
        <label for="input5">{{nomerRahunku}}</label>
        <input id="input5" v-model="teritoryBill"/>
      </div>
      <div>
        <label for="input6">{{summa}}</label>
        <input id="input6" v-model="teritoryBillSumm"/>
      </div>
    </div>

    <h3>оренда</h3>
    <div class="divFlex">
      <div>
        <label for="input7">{{nomerRahunku}}</label>
        <input id="input7" v-model="rentBill"/>
      </div>
      <div>
        <label for="input8">{{summa}}</label>
        <input id="input8" v-model="rentBillSumm"/>
      </div>
    </div>


    <h1>Форма</h1>
    <table>
      <tr>
        <td>Відшкодування комунальних витрат за {{currentMounth}} від {{orgLabel}} рах №сф-{{utilityBill}} від {{fromDate}}</td>
        <td class="paymentVal">{{utilityBillSumm}}</td>
      </tr>
      <tr>
        <td>Відшкодування витрат за користування земельною ділянкою за {{nextMounth}} від {{orgLabel}} рах №сф-{{teritoryBill}}  від {{fromDate}}</td>
        <td class="paymentVal">{{teritoryBillSumm}}</td>
      </tr>
      <tr>
        <td>Оренда приміщення за {{nextMounth}} від {{orgLabel}} рах №сф-{{rentBill}} від {{fromDate}}</td>
        <td class="paymentVal">{{rentBillSumm}}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: 'PaymentPattern',
  data() {
    return {
        orgLabel: '',
        nomerRahunku: 'номер рахунку',
        summa: "сума",
        fromDate: this.getPreviosDate (),
        currentMounth:this.getCurrentDate(),
        nextMounth:this.getNextDate(),
        utilityBill:"",
        utilityBillSumm: 0,
        teritoryBill:"",
        teritoryBillSumm: 0,
        rentBill:"",
        rentBillSumm: 0
    }
  },
  methods: {
      getPreviosDate()
      {
          let currDate = new Date();
          let strDate = "20"+"."+currDate.getMonth().toString()+'.'+currDate.getFullYear().toString();
          return strDate;
      },
      getCurrentDate()
      {
          let currDate = new Date();
          let strDate = (currDate.getMonth()+1).toString()+'.'+currDate.getFullYear().toString();
          return strDate;
      },
      getNextDate()
      {
          let currDate = new Date();
          let strDate = (currDate.getMonth()+2).toString()+'.'+currDate.getFullYear().toString();
          return strDate;
      },
  },
  mounted() {
      console.log('App mounted!');
      if (localStorage.getItem('orgLabel')) this.orgLabel = JSON.parse(localStorage.getItem('orgLabel'));
      if (localStorage.getItem('utilityBillSumm')) this.utilityBillSumm = JSON.parse(localStorage.getItem('utilityBillSumm'));
      if (localStorage.getItem('teritoryBillSumm')) this.teritoryBillSumm = JSON.parse(localStorage.getItem('teritoryBillSumm'));
      if (localStorage.getItem('rentBillSumm')) this.rentBillSumm = JSON.parse(localStorage.getItem('rentBillSumm'));
  },
  watch: {
      orgLabel: {
          handler() {
              console.log('orgLabel changed!');
              localStorage.setItem('orgLabel', JSON.stringify(this.orgLabel));
          },
          // deep: true,
      },utilityBillSumm: {
          handler() {
              console.log('utilityBillSumm changed!');
              localStorage.setItem('utilityBillSumm', JSON.stringify(this.utilityBillSumm));
          },
          // deep: true,
      },teritoryBillSumm: {
          handler() {
              console.log('teritoryBillSumm changed!');
              localStorage.setItem('teritoryBillSumm', JSON.stringify(this.teritoryBillSumm));
          },
          // deep: true,
      },rentBillSumm: {
          handler() {
              console.log('rentBillSumm changed!');
              localStorage.setItem('rentBillSumm', JSON.stringify(this.rentBillSumm));
          },
          // deep: true,
      },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.orgLabel{
  width: 150px;
}
.paymentVal{
  padding-left: 10px;
  text-align: right;
}
.divFlex{
  display: flex;
  flex-wrap: wrap;
}
h3 {
  margin: 10px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
input{
  margin: 5px 5px 5px;
  width: 70px;
}
.checkForm{
  text-align: left;
}
</style>