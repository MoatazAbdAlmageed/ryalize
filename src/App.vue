<script setup></script>
<template>
      <button @click="showUsers">Users</button>
      <table>
    <thead>
    <tr>
      <th>ID</th>
      <th>Name</th>
      <th>Email</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="user in users" :key="user.id">
      <td>{{ user.id }}</td>
      <td>{{ user.name }}</td>
      <td>{{ user.email }}</td>
     
    </tr>
 
  </tbody>
</table>
      <button @click="showProducts">Products</button>
      <table>
    <thead>
    <tr>
      <th>ID</th>
      <th>Name</th>

    </tr>
  </thead>
  <tbody>
    <tr v-for="product in products" :key="product.id">
      <td>{{ product.id }}</td>
      <td>{{ product.name }}</td>
    </tr>
 
  </tbody>
</table>
      <button @click="showTransactions">Transactions</button>
      <table>
    <thead>
    <tr>
      <th>ID</th>
      <th>Amount</th>
      <th>User</th>
      <th>Product</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="transaction in transactions" :key="transaction.id">
       
      <td>{{ transaction.id }}</td>
      <td>{{ transaction.user }}</td>
      <td>{{ transaction.amount }}</td>
      <td>{{ transaction.product }}</td>
    
    </tr>
 
  </tbody>
</table>
</template>

<script>
export default {
  data() {
    return {
      products: [],
      users: [],
      transactions: [],
    };
  },
  methods: {
    showUsers() {
      this.products=[];
      this.transactions=[];
      fetch("http://localhost:8080/users")
        .then((response) => response.json())
        .then((data) => (this.users = data));
    }, showProducts() {
      this.user=[];
      this.transactions=[];
      fetch("http://localhost:8080/products")
        .then((response) => response.json())
        .then((data) => (this.products = data));
    }, showTransactions() {
      this.products=[];
      this.users=[];
      fetch("http://localhost:8080/transactions")
        .then((response) => response.json())
        .then((data) => (this.transactions = data));
    },
  },
};
</script>