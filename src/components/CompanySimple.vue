<template>
  <div id="app">
    <div class="card">
      <header class="card-header">
        <p class="card-header-title">{{name}}</p>
        <a href="#" class="card-header-icon" aria-label="more options">
          <span class="icon">
            <i class="fas fa-angle-down" aria-hidden="true"></i>
          </span>
        </a>
      </header>
      <div class="card-content">
        <div class="content">
          <p>ID {{id}}</p>

        </div>
      </div>
      <footer class="card-footer">
        <a href="#" class="card-footer-item">Edit</a>
      </footer>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CompanySimple',
  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
  },
};
</script>
