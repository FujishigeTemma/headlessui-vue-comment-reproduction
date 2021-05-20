<template>
  <div>
    <h1>OK</h1>
    <Listbox v-model="selectedPerson">
      <ListboxButton>{{ selectedPerson.name }}</ListboxButton>
      <ListboxOptions>
        <ListboxOption
          v-for="person in people"
          :key="person"
          :value="person"
          :disabled="person.unavailable"
        >
          {{ person.name }}
        </ListboxOption>
      </ListboxOptions>
    </Listbox>
  </div>
  <div>
    <h1>Error</h1>
    <Listbox v-model="selectedPerson">
      <ListboxButton>{{ selectedPerson.name }}</ListboxButton>
      <ListboxOptions>
        <ListboxOption
          v-for="person in people"
          :key="person"
          :value="person"
          :disabled="person.unavailable"
          as="template"
        >
          <!-- some comment -->
          {{ person.name }}
        </ListboxOption>
      </ListboxOptions>
    </Listbox>
  </div>
</template>

<script>
  import { ref } from 'vue'
  import {
    Listbox,
    ListboxButton,
    ListboxOptions,
    ListboxOption,
  } from '@headlessui/vue'

  export default {
    components: { Listbox, ListboxButton, ListboxOptions, ListboxOption },

    setup() {
      const people = [
        { id: 1, name: 'Durward Reynolds', unavailable: false },
        { id: 2, name: 'Kenton Towne', unavailable: false },
        { id: 3, name: 'Therese Wunsch', unavailable: false },
        { id: 4, name: 'Benedict Kessler', unavailable: true },
        { id: 5, name: 'Katelyn Rohan', unavailable: false },
      ]
      const selectedPerson = ref(people[0])

      return {
        people,
        selectedPerson,
      }
    },
  }
</script>
