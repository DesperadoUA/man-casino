<template>
  <header>
    <div class="container header_container">
      <app_logo />
      <div class="header_right_part">
      <app_menu />
      <app_search />
      </div>
    </div>
  </header>
</template>
<script>
    import app_logo from './app-logo'
    import app_menu from './app-menu'
	import app_search from './app-search'
    export default {
        name: "app-header",
        data(){
            return {
                options: {}
            }
        },
        components: {app_logo, app_menu, app_search},
        async mounted(){
          await this.$store.dispatch('options/setOptions')
          const options = this.$store.getters['options/getOptions']
          this.options = options
        }
    }
</script>

<style>
    header{
      width: 100%;
      box-sizing: border-box;
        background: var(--strong-blue);
        padding-top: 5px;
        padding-bottom: 5px;
    }
  .header_container {
    padding: 10px 0px;
    display: flex;
    justify-content: space-between;
  }
  .header_right_part {
    display: flex;
  }
</style>