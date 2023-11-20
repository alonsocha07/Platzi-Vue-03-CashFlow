<template>
     <div class="movement">
        <div class="content">
            <h4>{{ titleRef }}</h4>
            <p>{{ descriptionRef }}</p>
        </div>
        <div class="action">
            <img src="@/assets/trash-icon.svg" alt="borrar" @click="remove" />
            <p :class="{
                'red': isNegative,
                'green': !isNegative
            }">{{ amountCurrency }}</p>

        </div>
    </div>
</template>

<script setup>
import { toRef, computed, defineEmits } from 'vue';

const props = defineProps({
    id: {
        type: Number,
    },
    title: {
        type: String,
    },
    description: {
        type: String,
    },
    amount: {
        type: Number,
    }
});
const idRef = toRef(props, 'id');
const titleRef = toRef(props, 'title');
const descriptionRef = toRef(props, 'description');
const amountRef = toRef(props, 'amount');
const emit = defineEmits(["remove"])


const currencyFormater = new Intl.NumberFormat("es-CR", {
  style: "currency", currency: "CRC"
})

const amountCurrency = computed(()=>
    currencyFormater.format(amountRef.value)
)

const remove = () => {
    emit("remove", idRef.value)
}

const isNegative = computed(()=>{
    if (amountRef.value > 0) {
        return false
    }else{
        return true
    }
})


</script>


<style scoped>
.movement {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 16px;
  background-color: #e6f9ff;
  border-radius: 8px;
  box-sizing: border-box;
}
.movement .content {
  width: 100%;
}
.movement .action {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  flex-direction: column;
}
h4,
p {
  margin: 0;
  padding: 0;
}
h4 {
  margin-bottom: 8px;
}
.movement .action img {
  margin-bottom: 16px;
}
.red {
    color: red;
}
.green {
    color: green;
}
</style>