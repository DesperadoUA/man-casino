<template>
    <section class="top_bonuses">
        <div class="container top_bonuses_container">
            <h2 class="top_bonuses_title" v-if="title">{{title}}</h2>
            <div class="top_bonuses_wrapper">
                <div class="top_bonuses_item"
                    v-for="(item, index) in value" :key="index" 
                    itemscope itemtype="http://schema.org/Event"
                >
                    <div class="top_bonuses_item_thumbnail">
                        <NuxtLink :to="item.permalink">
                            <img :src="item.thumbnail" 
                                 itemprop="image"
                                 loading="lazy" 
                                 width="145" 
                                 height="110">
                        </NuxtLink>
                    </div>
                    <div class="top_bonuses_item_title">
                        {{item.title}}
                    </div>
                    <div class="top_bonuses_item_bonus_value">
                        <span itemprop="name" style="display:inline-block">{{item.sub_title}}</span> : <span class="color-gold">{{item.value}}</span>
                    </div>
                     <div class="top_bonuses_item_data">
                        з <span itemprop="startDate" :datetime="item.start">{{item.start}}</span> по <span itemprop="endDate" :datetime="item.end">{{item.end}}</span>
                    </div>
                    <div class="bonus_item_author hide" itemprop="performer" itemscope itemtype="http://schema.org/Person">
                        <span itemprop="name">Автор: {{item.name}}</span>
                    </div>
                    <div class="top_bonuses_item_short_desc" itemprop="description">
                        {{item.short_desc}}
                    </div>
                    <div style="display:none" itemprop="location" itemscope itemtype="http://schema.org/VirtualLocation" >
	              Сайт: <span itemprop="url">{{item.site}}</span>
	            </div>
                <meta itemprop="eventStatus" content="https://schema.org/EventScheduled">
                <meta itemprop="eventAttendanceMode" content="https://schema.org/OnlineEventAttendanceMode">
                <span itemprop="organizer" itemscope="" itemtype="https://schema.org/Organization">
                    <meta itemprop="name" content="onlinecasino.men">
                    <meta itemprop="url" content="onlinecasino.men">
                </span>
                <span itemprop="offers" itemscope="" itemtype="https://schema.org/Offer">
                    <meta itemprop="Price" content="0">
                    <meta itemprop="priceCurrency" content="UAH">
                    <meta itemprop="url" :content="item.site">
                    <link itemprop="availability" href="https://schema.org/InStock">
                    <meta itemprop="validFrom" content="2021-08-10 08:00:00+03:00">
                </span>
                    <button class="top_bonuses_item_button" @click="refActivate(item)">
                        Отримати бонус
                    </button>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
	export default {
		name: "app_top_bonuses",
        props: {
			value: {
				type: Array,
                default: [],
            },
            title: {
				type: String,
                default: undefined
            }
        },
		methods: {
			refActivate(item) {
                if(item.ref.length !== 0) {
                    const min = 0
                    const max = item.ref.length - 1
                    const random = Math.floor(Math.random() * (max - min + 1)) + min
                    window.open(item.ref[random].event_ref, '_blank')
                } 
            }
		}
	}
</script>

<style scoped>
.top_bonuses {
    padding: 30px 0px;
    background: var(--light-black);
    overflow: hidden;
}
    .top_bonuses_title {
        font-family: var(--font);
        color: var(--white);
        margin-bottom: 22px;
        font-size: 28px;
    }
    .top_bonuses_item_data {
        font-family: var(--font);
        color: var(--white);
        background: var(--fiolet);
        padding: 5px;
        text-align: center;
    }
    .top_bonuses_item {
        width: 290px;
        background: var(--strong-blue);
        border-radius: 10px;
        overflow: hidden;
        margin-bottom: 15px;
    }
    .top_bonuses_wrapper {
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
    }
    .top_bonuses_item_thumbnail {
        padding: 10px;
        text-align: center;
    }
    .top_bonuses_item_title {
        padding: 0px 5px 15px;
        font-family: var(--font);
        font-size: 16px;
        color: var(--white);
        text-align: center;
        background: var(--strong-blue);
    }
    .top_bonuses_item_bonus_value {
        text-align: center;
        background: var(--fiolet);
        padding: 15px 10px 5px 10px;
        color: var(--white);
        font-family: var(--font);
        border-top-left-radius: 10px;
        border-top-right-radius: 10px;
    }
    .top_bonuses_item_bonus_value span {
        display: block;
        font-weight: bolder;
    }
    .top_bonuses_item_short_desc {
        background: var(--fiolet);
        padding: 5px 15px;
        color: var(--white);
        font-family: var(--font);
        font-size: 12px;
        height: 180px;
        overflow: hidden;
        border-bottom-left-radius: 10px;
        border-bottom-right-radius: 10px;
        z-index: 2;
        position: relative;
    }
    .top_bonuses_item_button {
        width: 100%;
        padding: 25px 15px 15px 15px;
        background: var(--green);
        font-family: var(--font);
        text-transform: uppercase;
        border: none;
        font-weight: bold;
        position: relative;
        z-index: 1;
        margin-top: -10px;
        cursor: pointer;
    }
    @media (min-width: 320px) and (max-width: 767px) {
        .top_bonuses_title {
            text-align: center;
            font-size: 28px;
        }
        .top_bonuses_wrapper {
            justify-content: center;
            margin-right: 0px;
            box-sizing: border-box;
        }
        .top_bonuses_item {
            min-width: 270px;
        }
        .top_bonuses_item:last-child {
            margin-right: 0px;
        }
        .top_bonuses_container {
            max-width: 100%;
            padding-left: 15px;
        }
        .top_bonuses_item_short_desc {
            height: auto;
        }
        .top_bonuses_container {
            padding-left: 0px;
        }
    }
    @media (min-width: 768px) and (max-width: 1200px) {
        .top_bonuses_wrapper {
            overflow-x: scroll;
        }
        .top_bonuses_item {
            min-width: 270px;
            margin-right: 20px;
        }
        .top_bonuses_item:last-child {
            margin-right: 0px;
        }
    }
</style>