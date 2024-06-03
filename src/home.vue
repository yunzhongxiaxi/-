<template>
  <my-header></my-header>
  <div style="display: flex;">
    <nav-menu style="width: 300px"></nav-menu>
    <el-container>
      <component :is="currentView" ></component>
    </el-container>
  </div>

</template>

<script>
import MyHeader from './components/header.vue'
import navMenu from "@/components/navMenu";
import goodsTable from "@/components/goodsTable";
import addGood from  '@/components/addGood'
import employeeTable from '@/components/employeeTable'
import addEmployee from '@/components/addEmployee'
import customerTable from '@/components/customerTable'
import addCustomer from "@/components/addCustomer";
import addRetail from '@/components/addRetail'
import orders from '@/components/orders'
import addWholesale from '@/components/addWholesale'
import stock from '@/components/stock'
import input from '@/components/input'
import allRepository from '@/components/allRepository'
import addRepository from '@/components/addRepository'
import {useRouter, useRoute, createRouter, createWebHistory} from 'vue-router'
import {createRouter as $router} from "vue-router/dist/vue-router.esm-browser";

const routes = {
  '/allGoods': goodsTable,
  '/addGood' : addGood,
  '/allEmployee' : employeeTable,
  '/addEmployee' : addEmployee,
  '/allCustomer' : customerTable,
  '/addCustomer' : addCustomer,
  '/addRetail' : addRetail,
  '/allOrders' : orders,
  '/addWholesale' :addWholesale,
  '/stock' : stock,
  '/input' : input,
  '/allRepository' :allRepository,
  '/addRepository' :addRepository,
}
export default {
  name: 'App',
  components: {
    MyHeader,navMenu,goodsTable,employeeTable,addEmployee,customerTable,addRetail,orders,addWholesale,input,allRepository,addRepository
  },
  data(){
    return{
      currentPath: window.location.hash,
    }
  },
  methods :{
    jump() {
      console.log(router.currentRoute)
    }
  },
  computed: {
    currentView() {
      return routes[this.currentPath.slice(1) || '/']
    }
  },
  mounted() {
    window.addEventListener('hashchange', () => {
      this.currentPath = window.location.hash
    })
  }
}
</script>

<style>

</style>
