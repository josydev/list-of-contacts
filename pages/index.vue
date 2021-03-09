<template>
  <div class="grid-template">
    <header class="leads">
      <Logo />
      <!-- <Logo dark-background /> -->
      <h1 class="leads__title"></h1>
    </header>

    <aside>
      <!-- <filter das categorias /> -->
      <h2>Categorias</h2>
      <ul @click="select = $event.target.dataset.value">
        <li data-value="">Todos</li>
        <li v-for="user of list" :key="user.id" :data-value="user.company.bs">
          {{ user.company.bs }}
        </li>
      </ul>
    </aside>

    <main>
      <!-- <filter de pesquisa /> -->
      <section class="section-search">
        <h2>Leads</h2>
        <input
          type="search"
          class="filter"
          @input="filter = $event.target.value"
        />
      </section>

      <!-- <Listando os Itens /> -->

      <article class="container-card">
        <Card
          v-for="user of listFilter"
          :key="user.id"
          :name="user.name"
          :username="user.username"
          :city="user.address.city"
          :phone="user.phone"
          :company="user.company.name"
          :setor="user.company.bs"
          :email="user.email"
        ></Card>
      </article>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      list: [],
      filter: '',
      select: '',
      teste: '',
    }
  },

  async fetch() {
    this.list = await fetch(
      'https://jsonplaceholder.typicode.com/users'
    ).then((res) => res.json())
  },

  computed: {
    listFilter() {
      if (this.filter) {
        const exp = new RegExp(this.filter.trim(), 'i')
        return this.list.filter((list) => exp.test(list.name))
      }
      if (this.select) {
        return this.list.filter((list) => list.company.bs === this.select)
      } else {
        return this.list
      }
    },
  },
}
</script>

<style lang="scss" scoped="true">
.leads {
  &__title {
    margin: 1.4rem 0;
    padding: 1.4rem 0;
    border-top: $border-color 1px solid;
  }
}
</style>
