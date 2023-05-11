<template>
  <header>
    <div class="">
      <Header name="Practice Pops and Emits" />
      <Information />
    </div>
    <!-- <RouterView /> -->
  </header>
</template>

<script>
import Header from '../src/components/Header.vue'
import Information from '../src/components/Information.vue'
import AddNewPerson from '../src/components/AddNewPerson.vue';

export default{
  name: 'App',
  components: {
    Header, Information, AddNewPerson,
  },
  data() {
    return {
    }
  },
}
</script>
