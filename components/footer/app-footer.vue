<template>
  <footer v-if="changeOptions !== null">
    <nav class="footer_menu" v-if="options.footer_menu.length !== 0">
      <div class="container">
        <ul>
          <li class="footer_menu_item"
              v-for="(item, index) in options.footer_menu"
                    :key="index">
                      <NuxtLink no-prefetch :to="item.permalink" >
                          {{item.title}}
                      </NuxtLink>
          </li>
        </ul>
      </div>
    </nav>
    <div class="footer_partners">
      <div class="container footer_partners_wrapper">
        <div class="footer_partners_left">
          <a v-for="(item, index) in options.partners"
             :key="index"
             :href="item.partners_link"
             target="_blank"
             class='partners_link'
             >
            <img loading="lazy"
                 :src='item.partners_img'
                 height="40"
             />
          </a>
        </div>
      </div>
    </div>
    <div class="container footer_container">
      <div class="footer_text">
        {{options.footer_text}}
        <img v-if="options.security_logo"
             :src="options.security_logo"
             class="security_logo dmca-badge"
             width="120"
             height="25"
             loading="lazy"
             title="DMCA.com Protection Status"
             />
      </div>
    </div>
    <GuardPopUp v-if="showGuardModal" />
  </footer>
</template>

<script>
import GuardPopUp from '~/components/guard_pop_up'
import { GUARD_MODAL_KEY, GUARD_COOKIE_STORAGE_KEY } from '@/constants.js'
import translateMixin from '~/mixins/translate.js'
    export default {
        name: "app-footer",
        data(){
            return {
               options: null
            }
        },
        mixins: [translateMixin],
        components: { GuardPopUp },
        computed: {
          changeOptions(){
            this.options = this.$store.getters['options/getOptions']
            return this.options
          },
          showGuardModal() {
            return this.$store.getters['modal/getModals'][GUARD_MODAL_KEY]
          }
        },
        mounted() {
          const headers = this.$store.getters['common/getHeaders']
          const cookie = headers.cookie || ''
          const guardHide = !cookie.includes(GUARD_COOKIE_STORAGE_KEY) ? false : true
          if(!guardHide) {
            this.$store.dispatch('modal/setStateModal', { key: GUARD_MODAL_KEY, status: true })
          }
        }
    }
</script>

<style>
.footer_menu {
  padding-top: 10px;
  padding-bottom: 10px;
}
.footer_menu_item {
  display: inline-block;
  padding: 10px;
}
.footer_menu_item a {
  color: var(--white);
  text-transform: uppercase;
  text-decoration: none;
  font-family: 'Open Sans Semi';
}
    footer {
      padding-bottom: 25px;
      color: var(--white);
      background: var(--strong-blue);
    }
    .footer_text {
      font-family: var(--font);
      font-style: normal;
      font-weight: normal;
      font-size: 15px;
      color: var(--white);
    }
    .footer_container {
      padding-top: 25px;
      position: relative;
    }
    .security_logo {
      position: absolute;
      top:25px;
      right: 10px;
    }
    .footer_partners {
      padding-bottom: 15px;
      padding-top: 15px;
      background: var(--middle-blue);
    }
    .footer_partners_wrapper {
      display: flex;
      justify-content: space-between;
    }
    .partners_link {
      height: 40px;
      display: inline-block;
      margin-left: 15px;
      margin-right: 15px;
    }
    .partners_link:nth-child(1) {
      margin-left: 0px;
    }
    .partners_link img {
      max-height: 100%;
    }

    @media (min-width: 320px) and (max-width: 767px) {
      .security_logo {
        margin-top: 10px;
        position: static;
      }
      .footer_partners_wrapper {
        flex-wrap: wrap;
      }
      .partners_link {
        margin-top: 5px;
        margin-bottom: 5px;
      }
      .footer_text {
        text-align: center;
      }
    }
</style>
