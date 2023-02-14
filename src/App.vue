<script lang="ts" setup>
import { ref } from 'vue';
import type { Ref } from 'vue'

const result = ref(0);
const operationArr: Ref<string[]> = ref([]);
const tempNumber = ref('');
const getNumber = (number: string) => {
  tempNumber.value += number;
};
const getOperation = (operation: string) => {
  operationArr.value.push(tempNumber.value);
  tempNumber.value = '';
  operationArr.value.push(operation);
};
const removeAll = () => {
operationArr.value = [];
tempNumber.value = '';
};
</script>
<template>
  <div class="bg-light h-100 d-flex">
    <div class="calculator bg-dark p-3">
      <h5 class="text-white">CALCULATOR</h5>
      <div class="screen text-end bg-light p-2">
        <div class="operation">
          <div v-if="operationArr.length">
            <span v-for="(item, index) of operationArr" :key="index">{{ item }}</span>
            <span>{{ tempNumber }}</span>
          </div>
          <div v-else>
            <span>{{ tempNumber }}</span>
          </div>
        </div>
        <div class="result-number h3 m-0">{{ result }}</div>
      </div>
      <div class="operations py-2 d-flex gap-2">
        <button class="btn btn-warning" @click="removeAll">AC</button>
        <button class="btn btn-secondary" @click="getOperation('+')"><i class="px-1 fa-solid fa-plus"></i></button>
        <button class="btn btn-secondary" @click="getOperation('-')"><i class="px-1 fa-solid fa-minus"></i></button>
        <button class="btn btn-secondary" @click="getOperation('*')"><i class="px-1 fa-solid fa-xmark"></i></button>
        <button class="btn btn-secondary" @click="getOperation('/')"><i class="px-1 fa-solid fa-divide"></i></button>
      </div>
      <div class="d-flex gap-2">
        <button class="btn btn-danger flex-fill" @click="getNumber('1')">1</button>
        <button class="btn btn-danger flex-fill" @click="getNumber('2')">2</button>
        <button class="btn btn-danger flex-fill" @click="getNumber('3')">3</button>
      </div>
      <div class="mt-2 d-flex gap-2">
        <button class="btn btn-danger flex-fill" @click="getNumber('4')">4</button>
        <button class="btn btn-danger flex-fill" @click="getNumber('5')">5</button>
        <button class="btn btn-danger flex-fill" @click="getNumber('6')">6</button>
      </div>
      <div class="mt-2 d-flex gap-2">
        <button class="btn btn-danger flex-fill" @click="getNumber('7')">7</button>
        <button class="btn btn-danger flex-fill" @click="getNumber('8')">8</button>
        <button class="btn btn-danger flex-fill" @click="getNumber('9')">9</button>
      </div>
      <div class="mt-2 d-flex gap-2">
        <button class="btn btn-danger flex-fill" @click="getNumber('0')">0</button>
        <button class="btn btn-danger flex-fill">.</button>
        <button class="btn btn-success flex-fill"><i class="fa-solid fa-equals"></i></button>
      </div>
    </div>
  </div>
</template>
