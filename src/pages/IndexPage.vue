<template>
  <q-page class="flex flex-center items-start">
    <div class="q-pa-xl">
      <div class="q-gutter-md flex flex-center q-mb-xl">
        <q-input
          class=""
          color="green"
          rounded
          v-model="text"
          placeholder="Qual chá procura?"
        >
          <template v-slot:append>
            <q-icon v-if="text === ''" name="search" />
            <q-icon
              v-else
              name="clear"
              class="cursor-pointer"
              @click="text = ''"
            /> </template
        ></q-input>
      </div>
      <div class="q-gutter-md row justify-around items-start">
        <TeaCard
          v-for="{
            ID,
            Name,
            Description,
            Benefits,
            Contraindication,
          } in teaMenu"
          :key="ID"
          :name="Name"
          :description="Description"
          :benefits="Benefits"
          :contraindications="Contraindication"
        />
      </div>
    </div>
  </q-page>
</template>

<script setup>
import { ref, reactive, computed, onMounted } from "vue";
import TeaCard from "components/teaCard.vue";
import axios from "axios";

const text = ref("");
const teaList = reactive([]);

const teaMenu = computed(() =>
  teaList.filter((tea) => {
    return tea.Name.toLowerCase().includes(text.value.toLowerCase());
  })
);

onMounted(() => {
  try {
    axios.get("https://fastapi-teas.vercel.app/teas").then((response) => {
      const data = response.data;
      teaList.push(...data);
    });
  } catch (error) {
    console.log(error);
  }
});
</script>
