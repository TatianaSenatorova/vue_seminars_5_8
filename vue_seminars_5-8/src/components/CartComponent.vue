<!-- Задача 2. Семинар 5. Разработать интерфейс корзины товаров, в котором пользователь 
может изменять количество товаров в корзине и видеть общую сумму 
покупки. Каждый товар представлен в виде блока, содержащего поле 
ввода для изменения количества товара и отображение его цены. При 
изменении количества товаров в поле ввода, необходимо 
автоматически пересчитывать стоимость каждого товара и обновлять 
общую сумму покупки.  -->

<template>
    <div>
        <ul>
            <li v-for="item in cart" :key="item.id">
                <p>{{ item.productName }}</p>
                <label>Enter quantity
                    <input type="number" v-model="item.quantity" @change="updateTotal">
                </label>
                <p>{{ item.price }}</p>
                <p>Subtotal<span> {{item.quantity * item.price}}</span></p>
            </li>
        </ul>
        <p>Total <span>{{ totalPrice }}</span></p>
    </div>

</template>

<script>
export default {
    name: 'CartComponent',
    data() {
        return {
            cart: [
                { id: 1, productName: 'product 1', price: '10', quantity: 1 },
                { id: 2, productName: 'product 2', price: '20', quantity: 1 },
                { id: 3, productName: 'product 3', price: '30', quantity: 1 },
            ],
            totalPrice: 0
        }


    },

    methods: {
        updateTotal() {
            this.totalPrice = this.cart.reduce((sum, item) => {return sum + item.price * item.quantity}, 0);
         
        }
    },
    mounted(){
        this.updateTotal();
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss"></style>