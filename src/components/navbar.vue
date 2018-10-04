<template>
<b-navbar toggleable="md" type="dark" variant="info" sticky="true">
  <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>
  <b-collapse is-nav id="nav_collapse">
    <b-navbar-nav>
      <b-nav-item href="#">НАЗАД</b-nav-item>
      <b-nav-item href="#">ВПЕРЁД</b-nav-item>
      <b-nav-item-dropdown text="Показать" right>
        <b-dropdown-item href="#">20 на странице</b-dropdown-item>
        <b-dropdown-item href="#">50 на странице</b-dropdown-item>
        <b-dropdown-item href="#">100 на странице</b-dropdown-item>
      </b-nav-item-dropdown>
    </b-navbar-nav>

    <b-navbar-nav class="ml-auto">
      <b-nav-form>
        <b-form-input size="sm" class="mr-sm-2" type="text" placeholder="Поиск"/>
        <b-button size="sm" class="my-2 my-sm-0" type="submit">Поиск товаров</b-button>
      </b-nav-form>
      
    </b-navbar-nav>
  </b-collapse>
</b-navbar>
</template>
<script>
	
</script>
<style scoped>
	
</style>