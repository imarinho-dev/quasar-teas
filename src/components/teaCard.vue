<template>
  <q-card
    class="max-w-sm transition-all duration-150 ease-in hover:drop-shadow-lg"
  >
    <q-card-section>
      <q-img
        class="rounded-borders"
        src="https://cdn.quasar.dev/img/parallax2.jpg"
      >
        <div class="text-h6 absolute-bottom text-center">
          {{ props.name }}
        </div>
      </q-img>

      <p class="text-subtitle1 q-mb-md">
        {{ props.description }}
      </p>
      <q-list bordered class="rounded-borders">
        <q-expansion-item
          group="teagroup"
          header-class="bg-green text-white"
          expand-icon-class="text-white"
          expand-separator
          label="Benefícios"
        >
          <q-card>
            <q-card-section>
              <ul v-for="(benefit, index) in props.benefits" :key="index">
                <li class="q-mb-md">
                  {{ benefit }}
                </li>
              </ul>
            </q-card-section>
          </q-card>
        </q-expansion-item>
        <q-separator color="green-4" />
        <q-expansion-item
          group="teagroup"
          header-class="bg-green text-white"
          expand-icon-class="text-white"
          expand-separator
          label="Contra-indicação"
        >
          <q-card>
            <q-card-section>
              <ul
                v-for="(contraindication, index) in props.contraindications"
                :key="index"
              >
                <li class="q-py-sm">
                  {{ contraindication }}
                </li>
              </ul>
            </q-card-section>
          </q-card>
        </q-expansion-item>
      </q-list>
    </q-card-section>
  </q-card>
</template>
<script setup>
const props = defineProps({
  name: String,
  description: String,
  benefits: Array,
  contraindications: Array,
});
</script>
