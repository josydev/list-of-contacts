<template>
  <div class="grid-template">
    <header class="contacts">
      <Logo />
      <h1 class="contacts__title">Prisma</h1>
      <!-- <Logo dark-background /> -->
    </header>

    <aside>
      <h2>Search</h2>

      <!-- Filtro dos nomes -->
      <input
        type="search"
        class="filter"
        placeholder="Search by name of your contact"
        @input="filter = $event.target.value"
      />

      <!-- <filtro das categorias /> -->
      <nav class="menu">
        <h3 class="menu__title" @click="show = !show">Company Categories</h3>
        <ul v-show="show" @click="select = $event.target.dataset.value">
          <li data-value="">Todos</li>
          <li v-for="user of list" :key="user.id" :data-value="user.company.bs">
            {{ user.company.bs }}
          </li>
        </ul>
      </nav>
    </aside>

    <main>
      <!-- <filter de pesquisa /> -->
      <section class="section-title">
        <h2>Contacts</h2>
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
          :website="user.website"
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
      show: true,
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

<style lang="scss" scoped="true"></style>
