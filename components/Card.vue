<template>
  <div class="card">
    <div class="card__header">
      <h2 class="card__title">{{ name }}</h2>
      <h3><span>@</span>{{ username }}</h3>
    </div>

    <div class="card__body">
      <h4>City</h4>
      <p>{{ city }}</p>
      <h4>Phone</h4>
      <p>{{ phone }}</p>
      <h4>Email</h4>
      <p>{{ email }}</p>
      <h4>Website</h4>
      <p>{{ website }}</p>
      <h4>Company</h4>
      <p>{{ company }}</p>
      <h4>Company Categorie</h4>
      <p>{{ setor }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      default: '-',
    },

    phone: {
      type: String,
      default: '-',
    },

    email: {
      type: String,
      default: '-',
    },

    website: {
      type: String,
      default: '-',
    },

    setor: {
      type: String,
      default: '-',
    },
    company: {
      type: String,
      default: '-',
    },

    city: {
      type: String,
      default: '-',
    },

    username: {
      type: String,
      default: '-',
    },
  },

  methods: {
    testClick() {
      this.indexOf()
    },
  },
}
</script>
