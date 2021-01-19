<template>
  <div class="card">
    <header class="card-header">
      <div class="control">
        <input
          class="input"
          type="text"
          placeholder="Text input"
          style="width: fit-content; height: fit-content"
          ref="name"
          :value="company.name"
        />
      </div>
    </header>
    <div class="card-content">
      <div class="content">
        <ul>
          <div class="control">
            <li>
              <span> id: </span>
              <input
                class="input"
                type="text"
                style="width: fit-content; height: fit-content"
                :value="company.id"
                ref="id"
              />
            </li>
          </div>
          <li>
            <span> Domain: </span>
            <input
              class="input"
              type="text"
              :value="company.domain"
              style="width: fit-content; height: fit-content"
              ref="domain"
            />
          </li>
          <li>
            <span>No. of Employees: </span>
            <input
              class="input"
              type="text"
              :value="company.numberOfEmployees"
              style="width: fit-content; height: fit-content"
              ref="numberOfEmployees"
            />
          </li>
          <li>
            <span
              >Subscription Per Employee:</span
            >
            <input
              class="input"
              type="text"
              :value="company.subscriptionsPerEmployees"
              style="width: fit-content; height: fit-content"
              ref="subscriptionsPerEmployee"
            />
          </li>
          <li>
            Total Subscriptions:
            {{ company.numberOfEmployees * company.subscriptionsPerEmployee }}
          </li>
        </ul>
        <br />
      </div>
    </div>
    <footer class="card-footer">
      <a href="#" class="card-footer-item" v-on:click="save">Save</a>
    </footer>
  </div>
</template>

<script>
import obj from '../services/CompanyService';

export default {
  name: 'Edit',
  async mounted() {
    this.company = await obj.getById(this.$route.params.id);
  },
  data() {
    return {
      company: {},
    };
  },
  methods: {
    save() {
      obj.ChangeObj({
        id: Number(this.$refs.id.value),
        name: this.$refs.name.value,
        domain: this.$refs.domain.value,
        subscriptionsPerEmployee: Number(this.$refs.subscriptionsPerEmployee.value),
        numberOfEmployees: Number(this.$refs.numberOfEmployees.value),
      });
      this.$router.push({ name: 'full', params: { id: this.company.id, message: 'Changes Successfully Saved!' } });
    },
  },
};
</script>

<style lang="scss">
.input {
  width: fit-content;
  height: fit-content;
}
</style>
