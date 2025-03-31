<template>
  <section :class="'content '+bg">
      <div class="container cms" v-html="value">
      </div>
  </section>
</template>

<script>
    export default {
        name: "app-content",
        props: {
        	value: {
        		type: String,
                default: ''
            },
            bg:{
        		type: String,
                default: ''
            }
        },
        data(){
            return {
                
            }
        },
         mounted(){
            const main = document.querySelector('.cms')
            const menu = main.querySelector('.nav')
            if(menu) {
                const arrH = []
                const h = main.querySelectorAll('.heading')
                h.forEach(item => {
                    arrH.push(item)
                })
               
                let str = '<div class="article_menu_heading">Зміст</div>' +
                          '<ol class="article_menu">'
                if(arrH.length === 0) {
                    menu.remove()
                } else {
                    arrH.forEach( (item, index) => {
                        str += `<li class="${item.dataset.deep}">
                      <a href="#heading_${index}">
                        ${item.innerHTML}
                      </a>
                    </li>`
                    })
                    str += '</ol>'
                    menu.insertAdjacentHTML('afterBegin', str)
                    arrH.forEach((item, index) => {
                        item.setAttribute('id', `heading_${index}`)
                    })
                }
            }
        }
    }
</script>
<style>
    .article_menu_heading {
        font-family: var(--font-bold);
        font-style: normal;
        font-size: 18px;
        line-height: 22px;
        text-decoration: none;
        color: var(--white);
    }
    .nav {
        padding: 15px 15px 5px 15px;
        border-radius: 12px;
        background: var(--light-black);
        margin-bottom: 20px;
        border: 1px solid var(--light-blue);
    }
    .second {
        margin-left: 15px;
    }
</style>