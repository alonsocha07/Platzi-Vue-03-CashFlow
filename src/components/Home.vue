<template>
    <Layout>
        <template #header>
            <Header></Header>
        </template>
        <template #resume>
            <Resume :label="'Ahorro Total'" :amount="amount" :totalAmount="totalAmount">
                <template #graphic>
                    <Graphic :amounts="amounts"/>
                </template>
                <template #action>
                    <Action/>
                </template>
            </Resume>
        </template>
        <template #movements>
            <Movements
            :movements="movements"
            />
        </template>
    </Layout>
</template>

<script setup>
import { ref } from "vue";

import Layout from "./Layout.vue"
import Header from "./Header.vue"
import Resume from "./Resume/index.vue"
import Movements from "./Movements/Index.vue"
import Action from "./Action.vue";
import Graphic from "./Resume/Graphic.vue";

const amount = ref(10000)
const totalAmount = ref(1800000)

const amounts= [100, 200, 500, 200, -400, -600 , 100 , 600];
const movements = [
        {
          id: 1,
          title: "Movimiento",
          description: "Deposito de salario",
          amount: 1000,
        },
        {
          id: 2,
          title: "Movimiento 1",
          description: "Deposito de honorarios",
          amount: 500,
        },
        {
          id: 3,
          title: "Movimiento 3",
          description: "Comida",
          amount: -100,
        },
        {
          id: 4,
          title: "Movimiento 4",
          description: "Colegiatura",
          amount: 1000,
        },
        {
          id: 5,
          title: "Movimiento 5",
          description: "Reparación equipo",
          amount: 1000,
        },
      ];
  
</script>