<template>
  <div id="app">
    <button class="btn" @click="openModal">Open Modal</button>
    <sweet-modal ref="modal">
      <div class="custom-content">
          <div class="header">
              <div class="danger-bar">
              </div>  
              <div class="header-title">
                <h2 class="text-left">Add New Expense</h2>
                <h4 class="text-right text-lightgray">UID: EXP1010-0001</h4>
              </div>          
          </div>
          <div class="modal-content">
              <div class="row">
                <div class="col-6">
                  <div class="form-group">
                    <label class="form-label text-gray" for="project">Project</label>
                    <CustomSelect :options="['123', '234', '334']" :placeholder="'Select Project'"/>
                  </div>
                </div>
                <div class="col-6">
                  <div class="form-group">
                    <label class="form-label text-gray" for="task">Task</label>
                    <CustomSelect :options="['123', '234', '334']" :placeholder="'Select Task'"/>
                  </div>
                </div>
              </div>
              <div class="row mt-20">
                <div class="col-6">
                  <div class="form-group">
                    <label class="form-label text-gray" for="vendor-name">Vendor Name</label>
                    <CustomSelect :options="['123', '234', '334']" :placeholder="'Select Vendor Name'"/>
                  </div>
                </div>
                <div class="col-6">
                  <div class="form-group">
                    <label class="form-label text-gray" for="vendor-tax-number">Vendor Tax Number</label>
                    <input class="form-control border-bottom" id="vendor-tax-number" placeholder=""/>
                  </div>
                </div>
              </div>

              <div class="row mt-20">
                <div class="col-6">
                  <div class="form-group">
                    <label class="form-label text-gray" for="vendor-name">Company Client</label>
                    <CustomSelect :options="['123', '234', '334']" :placeholder="'Select Company Client'"/>
                  </div>
                </div>
                <div class="col-6">
                  <div class="form-group">
                    <label class="form-label text-gray" for="group-name">Group / Trip Name</label>
                    <input class="form-control border-bottom" id="group-name" placeholder=""/>
                  </div>
                </div>
              </div>

              <div class="row mt-20">
                <div class="col-6">
                  <div class="form-group">
                    <label class="form-label text-gray" for="expense-item">Expense Item</label>
                    <CustomSelect :options="['123', '234', '334']" :placeholder="'Select Item'"/>
                  </div>
                </div>
                <div class="col-6">
                  <div class="form-group">
                    <label class="form-label text-gray" for="expense-date">Expense Date</label>
                    <date-pick v-model="date" :displayFormat="'DD / MM / YYYY'"></date-pick>
                  </div>
                </div>
              </div>

              <div class="row mt-20">
                <div class="col-6">
                  <div class="form-group">
                    <label class="form-label text-gray" for="amount">Amount</label>
                    <input class="form-control text-right border-bottom" id="amount" placeholder="44.00"/>
                  </div>
                </div>
                <div class="col-6">
                  <div class="form-group horizental justify-space-between">
                    <div class="btn-group">
                      <label class="btn-container text-gray" for="reimbursable">reimbursable
                        <input type="checkbox" name="reimbursable" id="reimbursable">
                        <span class="checkmark"></span>
                      </label>
                    </div>
                    <div class="btn-group">
                      <label class="btn-container text-gray" for="billable">Billable
                        <input type="checkbox" name="billable" id="billable">
                        <span class="checkmark"></span>
                      </label>                      
                    </div>
                  </div>
                </div>
              </div>
              
              <div class="row mt-20">
                <div class="col-6">
                  <div class="form-group">
                    <label class="form-label text-gray" for="tax">Tax</label>
                    <CustomSelect :options="['123', '234', '334']" :placeholder="'Select Tax'"/>
                  </div>
                </div>
                <div class="col-6">
                  <div class="form-group horizental justify-space-between">
                    <div class="btn-group">
                      <label class="btn-container text-gray" for="inclusive">Inclusive
                        <input type="radio" name="tax-status" id="inclusive">
                        <span class="radiomark"></span>
                      </label>                      
                    </div>
                    <div class="btn-group">
                      <label class="btn-container text-gray" for="exclusive">exclusive
                        <input type="radio" name="tax-status" id="exclusive">
                        <span class="radiomark"></span>
                      </label>                      
                    </div>
                  </div>
                </div>
              </div>
              <div class="custom-row mt-20">
                <label class="notes-label text-gray" for="notes">Notes</label>
                <div class="total-panel custom-row justify-space-between">
                  <span class="sum-title ml-23 text-gray">Total</span>
                  <span class="sum-num mr-21 font-weight-bold">44.00</span>
                </div>
              </div>
              <div class="row">
                  <textarea name="" id="notes" cols="30" rows="10" class="notes"/>
              </div>
              <div class="mt-20 text-right pl-21 pr-21">
                  <button class="btn mr-15">Cancel</button>
                  <button class="btn">Save</button>
              </div>
          </div>
      </div>   
    </sweet-modal>
  </div>
</template>

<script>
import DatePick from 'vue-date-pick';
import 'vue-date-pick/dist/vueDatePick.css';
import CustomSelect from "./components/CustomSelect.vue";
export default {
  name: 'app',
  components: {
    DatePick,
    CustomSelect
  },
  data() {
    return  {
      date: '',
      project: true,
      task: true,
      tax: true,
      vendorName: true,
      companyClient: true,
      expenseItem: true,
    }
  },
  methods:{
    openModal(){
      this.$refs.modal.open();
    },
    closeModal(){
      this.$refs.modal.close();
    }
  },
  mounted(){
    // var closeButton = document.querySelector('.sweet-action-close');
    // var child = closeButton.ChildNode.remove();
    // console.log(child)
  }
}
</script>

<style>
.vdpComponent{
  width: 100%;
}
.vdpComponent input{
  width: 100%;
  padding: 0 !important;
  outline: none;
  background-size: auto;
  border: none;
  border-bottom: solid 1px;
  background: url(./assets/calendar.png) no-repeat center left;
  text-indent: 20px;
}
.vdpClearInput{
  outline: none;
}
.vdpClearInput:before {
  line-height: 1.4em !important;
  color: black;
}
#app {
  font-family: 'Roboto';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.sweet-modal{
  padding: 19px 35px !important;
  background: #e8f0f7 !important;
}
.sweet-modal .sweet-box-actions{
    top: 22px !important;
    right: 40px !important;
}
.sweet-content{
  background: white !important;
  border-radius: 10px;
  padding: 28px 0 !important;
}
.close-btn{
  display: block;
  width: 25px;
  height: 25px;
  cursor: pointer;
  background: url(./assets/close.png) no-repeat center center;
  background-size: contain !important;
  transition: 0.3s;
}
.close-btn:hover{
  transform: scale(1.2);
}
.detail {
  margin-bottom: 50px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 20px;
}
.header {
  display: flex;
  height: 45px;
  align-items: center;
}
.header .danger-bar{
  width: 5px;
  height: 100%;
  border-radius: 2px;
  background: #ff8f8f;
  position: relative;
  left: -2px;
}
.header .header-title{
  display: flex;
  width: 100%;
  height: 100%;
  align-items: center;
  padding: 0 30px;
}
.header .header-title h4{
  margin-left: auto;
  font-size: 15px;
  font-weight: 400;
}
.modal-content{
  margin-top: 45px;
  padding: 0 9px;
}
.mt-20{
  margin-top: 20px !important;
}
.mr-21{
  margin-right: 21px !important;
}
.pr-21{
  padding-right: 21px !important;
}
.pl-21{
  padding-left: 21px !important;
}
.ml-23{
  margin-left: 23px !important;
}
.mr-15{
  margin-right: 15px !important;
}
.row,
.custom-row{
  display: flex;
  align-items: flex-end;
}
.col-6{
  width: 50%;
}
@media only screen and (max-width: 470px){
  .row{
    display: block;
  }
  .col-6{
    width: 100%;
    margin-top: 20px;
  }
}
.col-12{
  width: 100%;
}
.form-group{
  padding: 0 21px;
}
.btn-group{
  display: flex;
  height: 100%;
  align-items: center;
  justify-content: space-around;
}
@media only screen and (max-width: 600px){
  .btn-group{
    width: 100%;
    justify-content: left !important;
  }
}
.btn-group label{
  text-transform: capitalize;
  cursor: pointer;
  font-size: 14px;
}
.horizental{
  display: flex !important;
  flex-wrap: wrap;
}
.form-label{
  display: block;
  width: 100%;
  text-align: left;
  cursor: pointer;
  text-transform: capitalize;
  font-size: 14px;
}
.border-bottom{
  border-bottom: solid 1px black !important;
}
.form-control{
  width: 100%;
  height: 28px;
  border: none;
  outline: none;
  box-sizing: border-box;
  color: black;
  font-size: 14px;
}
::placeholder {
  color: black;
  font-weight: bold;
}

.btn-container {
  display: block;
  position: relative;
  padding-left: 21px;
  cursor: pointer;
  font-size: 22px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
/* Hide the browser's default checkbox */
.btn-container input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

/* Create a custom checkbox */
.checkmark {
  position: absolute;
  top: 2px;
  left: 0;
  height: 12px;
  width: 12px;
  background-color: #fff;
  border: solid 1px #c4c4c4;
}
/* Create the checkmark/indicator (hidden when not checked) */
.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}
/* Show the checkmark when checked */
.btn-container input:checked ~ .checkmark:after {
  display: block;
}

/* Style the checkmark/indicator */
.btn-container .checkmark:after {
  left: 3px;
  top: 1px;
  width: 3px;
  height: 7px;
  border: solid black;
  border-width: 0 2px 2px 0;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
}
/* Create a custom radio button */
.radiomark {
  position: absolute;
  top: 3px;
  left: 0;
  height: 11px;
  width: 11px;
  background-color: #fff;
  border-radius: 50%;
  border: solid 1px #c4c4c4;
}

/* Create the indicator (the dot/circle - hidden when not checked) */
.radiomark:after {
  content: "";
  position: absolute;
  display: none;
}

/* Show the indicator (dot/circle) when checked */
.btn-container input:checked ~ .radiomark:after {
  display: block;
}

/* Style the indicator (dot/circle) */
.btn-container .radiomark:after {
  top: 3px;
  left: 3px;
  width: 5px;
  height: 5px;
  border-radius: 50%;
  background: black;
}
.text-lightgray{
  color: #b5b5b5;
}
.notes-label{
  display: block;
  width: 50%;
  text-align: left;
  font-size: 14px;
  line-height: 30px;
  padding-left: 21px;
}
.total-panel{
  width: 50%;
  line-height: 30px;
  display: flex;
  height: 30px;
  align-items: start;  
}
.notes{
  padding: 10px;
  outline: none;
  appearance: none;
  border-radius: 10px;
  margin: 0 21px;
  height: 100px;
  background-color: #f8f8f8;
  box-sizing: border-box;
  border: none;
  font-size: 12px;
  width: calc(100% - 42px);
}
.text-left {
  text-align: left;
}
.text-right {
  text-align: right;
}
.btn-group {
  display: flex;
  justify-content: space-between;
}
.text-gray{
  color: #777777 !important;
}
.btn{
  outline: none;
  border-radius: 5px;
  padding: 8px 20px;
  text-align: center;
  cursor: pointer;
  height: 32px;
  font-size: 16px;
  color: #636363;
  font-weight: 500;
  font-family: 'Roboto';
  border: none;
  background-color: #ececec;
}
.justify-right{
  justify-content: right;
}
.font-weight-bold{
  font-weight: bold;
}
.sum-title,
.sum-num{
  text-transform: capitalize;
  display: block;
  color: black;
  font-size: 14px !important;
  line-height: 14px;
}
.justify-space-between{
  justify-content: space-between;
}
input[type='checkbox'],
input[type='radio']{
  cursor: pointer;
}
</style>
