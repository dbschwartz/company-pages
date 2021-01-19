<template>
  <div id="app">
    <company-simple v-for="company in companies"
      :id="company.id"
      :name="company.name"
      :key="company.id">
    </company-simple>
  </div>
</template>

<script>
import obj from '../services/CompanyService';
import CompanySimple from '../components/CompanySimple.vue';

export default {
  components: { CompanySimple },
  name: 'List',
  async mounted() {
    this.companies = await obj.getAll();
  },
  data() {
    return {
      companies: [],
    };
  },
};
</script>
