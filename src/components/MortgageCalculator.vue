<template>
  <div class="mortgage-calculator">
        <div class="mortgage-calculator__header">
            <div class="mortgage-calculator__title">Mortgage Calculator</div>
            <div class="mortgage-calculator__icon"></div>
        </div>
        <div class="mortgage-calculator__body">
            <form class="row">
                <div class="col-4 mb-3">
                    <label class="form-label" >Purchase price</label>
                    <input type="number" class="form-control" v-model="purchasePrice">
                </div>
                <div class="col-4 mb-3">
                    <label class="form-label">Down payment</label>
                    <input type="number" class="form-control" v-model="downPayment">
                </div>
                <div class="col-4 mb-3">
                    <label class="form-label">Payment time</label>
                    <input type="number" class="form-control" v-model="paymentTime" >
                </div>
                <div class="col-4 mb-3">
                    <label class="form-label">Interest rate</label>
                    <input type="number" class="form-control" v-model="interestRate" >
                </div>
                <div class="col-4 mb-3">
                    <label class="form-label">Loan amount</label>
                    <input type="number" class="form-control" v-model="loanAmount" >
                </div>
                <div class="col-4 mb-3">
                    <label class="form-label">Estimated per month</label>
                    <input type="number" class="form-control" v-model="estimatedPerMonth" >
                </div>
            </form>
        </div>
        <div class="mortgage-calculator__footer">
            <div class="mortgage-calculator__actions">
                <button class="" @click="calculate">Calculate</button>
            </div>
        </div>
    </div>                    
</template>  

<script lang="ts" setup>
  import { ref } from 'vue';                                
  const purchasePrice = ref(0)
  const downPayment = ref(0)      
  const paymentTime = ref(0)
  const interestRate = ref(0)
  const loanAmount = ref(0)
  const estimatedPerMonth = ref(0) 
  
  const calculate = ()=>{
    loanAmount.value = purchasePrice.value - downPayment.value;
    const P = loanAmount.value;
    const r = interestRate.value / 100 / 12;
    const n = paymentTime.value * 12;
    estimatedPerMonth.value = Math.round((P * r) * (Math.pow((1 + r), n)) / (Math.pow((1 + r), n) - 1));
  }
</script>
<style lang="scss">
.mortgage-calculator {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  $self: &;
  &__header {
    display: flex;
    flex-direction: row;
    padding: 15px;
    #{$self}__title {
        flex-grow: 1;
        font-size: 1.2rem;
        font-weight: 600;
    }
    #{$self}__icon {
        flex-grow: 0;
        font-size: 0.8rem;
    }
  }
  &__body {
    padding: 15px;
    font-size: 0.8rem;
    font-weight: 500;
    flex-grow: 1;
  }
  &__footer {
    display: flex;
    flex-direction: row;
    justify-content: center;
    padding: 15px;
    #{$self}__actions {
        button {
            align-items: center;
            background-color: #FFFFFF;
            border: 1px solid rgba(0, 0, 0, 0.1);
            border-radius: .25rem;
            box-shadow: rgba(0, 0, 0, 0.02) 0 1px 3px 0;
            box-sizing: border-box;
            color: rgba(0, 0, 0, 0.85);
            cursor: pointer;
            display: inline-flex;
            font-family: system-ui,-apple-system,system-ui,"Helvetica Neue",Helvetica,Arial,sans-serif;
            font-size: 16px;
            font-weight: 600;
            justify-content: center;
            line-height: 1.25;
            margin: 0;
            min-height: 3rem;
            padding: calc(.875rem - 1px) calc(1.5rem - 1px);
            position: relative;
            text-decoration: none;
            transition: all 250ms;
            user-select: none;
            -webkit-user-select: none;
            touch-action: manipulation;
            vertical-align: baseline;
            width: auto;
        }

        button:hover,
        button:focus {
         border-color: rgba(0, 0, 0, 0.15);
         box-shadow: rgba(0, 0, 0, 0.1) 0 4px 12px;
         color: rgba(0, 0, 0, 0.65);
        }
    
        button:hover {
         transform: translateY(-1px);
        }
    
        button:active {
         background-color: #F0F0F1;
         border-color: rgba(0, 0, 0, 0.15);
         box-shadow: rgba(0, 0, 0, 0.06) 0 2px 4px;
         color: rgba(0, 0, 0, 0.65);
         transform: translateY(0);
        }
       }
     }
}
</style>                                           

