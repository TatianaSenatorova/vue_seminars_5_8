<!-- Задача 3. Семинар 5. 
1. Создайте компонент MortgageCalculator с соответствующим шаблоном и скриптом.
2. В шаблоне компонента разместите поля ввода для суммы кредита, процентной 
ставки и срока кредита, а также элементы для отображения ежемесячного платежа 
и общей суммы выплаты.
3. Используйте директиву v-model для связывания введенных пользователем 
значений с соответствующими свойствами в компоненте.
4. Создайте вычисляемое свойство monthlyPayment, которое будет вычислять 
ежемесячный платеж на основе введенных значений суммы кредита, процентной 
ставки и срока кредита.
5. Создайте вычисляемое свойство totalPayment, которое будет вычислять общую 
сумму выплаты по кредиту, учитывая ежемесячный платеж и срок кредита.
6. Отобразите значения monthlyPayment и totalPayment в соответствующих элементах 
шаблона -->

<template>
    <div>
        <form>
            <label>Сумма кредита: <input type="number" v-model="loanAmount"></label>
            <label>Процентная ставка: <input type="number" v-model="interestRate"></label>
            <label>Срок кредита: <input type="number" v-model="loanTerm"></label>
            <p>Ежемесячный платеж: {{ monthlyPayment }}</p>
            <p>Общая сумма платежа: {{ totalPayment }}</p>
        </form>
    </div>

</template>

<script>
export default {
    name: 'MortgageCalculatorComponent',
    data() {
        return {
            loanAmount: 0,
            interestRate: 0,
            loanTerm: 0
        }
    },
    
    computed: {
        monthlyPayment() {
            const rate = this.interestRate / 100 / 12;
            const term = this.loanTerm;
            const principal = this.loanAmount;
            const numerator = rate * Math.pow(1 + rate, term);
            const denominator = Math.pow(1 + rate, term) - 1;
            const payment = principal * (numerator / denominator);
            return payment.toFixed(2);
        },
        totalPayment() {
            const term = this.loanTerm;
            const payment = parseFloat(this.monthlyPayment);
            return term * payment;
        },
    },
    mounted(){
        this.monthlyPayment();
        this.totalPayment();
    }
}


