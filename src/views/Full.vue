<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title">
        {{ company.name }}
      </p>
      <a href="#" class="card-header-icon" aria-label="more options">
        <span class="icon">
          <i class="fas fa-angle-down" aria-hidden="true"></i>
        </span>
      </a>
    </header>
    <div class="card-content">
      <div class="content">
        <ul>
          <li>id: {{ company.id }}</li>
          <li>Domain: {{ company.domain }}</li>
          <li>No. of Employees: {{ company.numberOfEmployees }}</li>
          <li>
            Subscription Per Employee: {{ company.subscriptionsPerEmployee }}
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
      <a href="#" class="card-footer-item">Edit</a>
    </footer>
  </div>
</template>

<script>
import obj from '../services/CompanyService';

export default {
  name: 'Full',
  async mounted() {
    this.company = await obj.getById(this.$route.params.id);
  },
  data() {
    return {
      company: {},
    };
  },
};
</script>
