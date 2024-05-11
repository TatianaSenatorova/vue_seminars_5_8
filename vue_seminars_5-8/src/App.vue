<template>
  <div id="app">
    <AuthenticationComponent></AuthenticationComponent>
    <CartComponent></CartComponent>
    <!-- <MortgageCalculatorComponent></MortgageCalculatorComponent> -->
    <ProductDetails></ProductDetails>
   
  </div>
</template>

<script>
import AuthenticationComponent from './components/AuthenticationComponent';
import CartComponent from './components/CartComponent';
// import MortgageCalculatorComponent from './components/MortgageCalculatorComponent';
import ProductDetails from './components/ProductDetails';



export default {
  name: 'App',
  components: {
    AuthenticationComponent,
    CartComponent,
    // MortgageCalculatorComponent, 
    ProductDetails
  },
  data() {
      return {
      
      };
  },
  
}

</script>

<style lang="scss">




</style>
