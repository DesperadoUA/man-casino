<template>
  <main>
      <app_banner />
      <!--<app_casino_loop :posts="data.body.casino"></app_casino_loop>-->
      <app_casino_loop :posts="top_casinos" title="Онлайн казино Украины" bg="bg-strong-black"/>
      <app_top_bonuses :value="bonuses" title="Топ бонусы" />
      <app_casino_loop :posts="casinos" bg="bg-strong-black"/>
      <app_content :value="data.body.content" bg="bg-strong-blue"/>
  </main>
</template>

<script>
    import DAL_Page from '~/DAL/static_pages'
    import app_content from '~/components/content/app-content'
    import app_casino_loop from '~/components/casino_loop/app_casino_loop'
    import app_banner from '~/components/banner/app_banner_main'
    import app_blog_card from '~/components/blog_card/app_blog_card'
    import app_top_bonuses from '~/components/top-bonuses/app_top_bonuses'
    import config from '~/config/index'
export default {
    name: "main-page",
    data: () => {
        return {
            casinos: [
				{
					title: '777 Original Обзор',
					ref: ['/ref-1', '/ref-2'],
					thumbnail: '/img/casino-logo.png',
					bonuses: [
						{
							bonuses_title: "Приветственный пакет",
							bonuses_sub_title: "Вейджер x40",
							bonuses_value: "24000 ₴ + 225FS"
						},
						{
							bonuses_title: "ТУРНИР-МАРАФОН",
							bonuses_sub_title: "Зависит от VIP-статуса",
							bonuses_value: "50 000 ₽"
						},
						{
							bonuses_title: "Вейджер",
							bonuses_sub_title: "Обмен CP на деньги",
							bonuses_value: "x30"
						}
					],
					short_desc: '(Описание бонуса) 4 bonuses up to €150 Terms & Conditions 18+. ' +
					'First 4 deposits of €10+. Certain deposit methods excluded.',
					licensed: [
						'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/krail_45.png',
						'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/curacao_45.png'
					],
					permalink: '/casino/link-1'
				},
				{
					title: '777 Original Обзор',
					ref: ['/ref-1', '/ref-2'],
					thumbnail: '/img/casino-logo.png',
					bonuses: [
						{
							bonuses_title: "Приветственный пакет",
							bonuses_sub_title: "Вейджер x40",
							bonuses_value: "24000 ₴ + 225FS"
						},
						{
							bonuses_title: "ТУРНИР-МАРАФОН",
							bonuses_sub_title: "Зависит от VIP-статуса",
							bonuses_value: "50 000 ₽"
						},
						{
							bonuses_title: "Вейджер",
							bonuses_sub_title: "Обмен CP на деньги",
							bonuses_value: "x30"
						}
					],
					short_desc: '(Описание бонуса) 4 bonuses up to €150 Terms & Conditions 18+. ' +
					'First 4 deposits of €10+. Certain deposit methods excluded.',
					licensed: [
						'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/krail_45.png',
						'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/curacao_45.png'
					],
					permalink: '/casino/link-1'
				},
				{
					title: '777 Original Обзор',
					ref: ['/ref-1', '/ref-2'],
					thumbnail: '/img/casino-logo.png',
					bonuses: [
						{
							bonuses_title: "Приветственный пакет",
							bonuses_sub_title: "Вейджер x40",
							bonuses_value: "24000 ₴ + 225FS"
						},
						{
							bonuses_title: "ТУРНИР-МАРАФОН",
							bonuses_sub_title: "Зависит от VIP-статуса",
							bonuses_value: "50 000 ₽"
						},
						{
							bonuses_title: "Вейджер",
							bonuses_sub_title: "Обмен CP на деньги",
							bonuses_value: "x30"
						}
					],
					short_desc: '(Описание бонуса) 4 bonuses up to €150 Terms & Conditions 18+. ' +
					'First 4 deposits of €10+. Certain deposit methods excluded.',
					licensed: [
						'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/krail_45.png',
						'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/curacao_45.png'
					],
					permalink: '/casino/link-1'
				},
				{
					title: '777 Original Обзор',
					ref: ['/ref-1', '/ref-2'],
					thumbnail: '/img/casino-logo.png',
					bonuses: [
						{
							bonuses_title: "Приветственный пакет",
							bonuses_sub_title: "Вейджер x40",
							bonuses_value: "24000 ₴ + 225FS"
						},
						{
							bonuses_title: "ТУРНИР-МАРАФОН",
							bonuses_sub_title: "Зависит от VIP-статуса",
							bonuses_value: "50 000 ₽"
						},
						{
							bonuses_title: "Вейджер",
							bonuses_sub_title: "Обмен CP на деньги",
							bonuses_value: "x30"
						}
					],
					short_desc: '(Описание бонуса) 4 bonuses up to €150 Terms & Conditions 18+. ' +
					'First 4 deposits of €10+. Certain deposit methods excluded.',
					licensed: [
						'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/krail_45.png',
						'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/curacao_45.png'
					],
					permalink: '/casino/link-1'
				},
				{
					title: '777 Original Обзор',
					ref: ['/ref-1', '/ref-2'],
					thumbnail: '/img/casino-logo.png',
					bonuses: [
						{
							bonuses_title: "Приветственный пакет",
							bonuses_sub_title: "Вейджер x40",
							bonuses_value: "24000 ₴ + 225FS"
						},
						{
							bonuses_title: "БОНУС \"WEDNESDAY\"",
							bonuses_sub_title: "Зависит от VIP-статуса",
							bonuses_value: "До 7%"
						},
						{
							bonuses_title: "Вейджер",
							bonuses_sub_title: "Обмен CP на деньги",
							bonuses_value: "x40"
						}
					],
					short_desc: '(Описание бонуса) 4 bonuses up to €150 Terms & Conditions 18+. ' +
					'First 4 deposits of €10+. Certain deposit methods excluded.',
					licensed: [],
					permalink: '/casino/link-2'
				},
				{
					title: '777 Original Обзор',
					ref: ['/ref-1', '/ref-2'],
					thumbnail: '/img/casino-logo.png',
					bonuses: [
						{
							bonuses_title: "Приветственный пакет",
							bonuses_sub_title: "Вейджер x40",
							bonuses_value: "24000 ₴ + 225FS"
						},
						{
							bonuses_title: "Кэшбэк от ваших ставок",
							bonuses_sub_title: "Зависит от VIP-статуса",
							bonuses_value: "До 7%"
						},
						{
							bonuses_title: "Вейджер",
							bonuses_sub_title: "Обмен CP на деньги",
							bonuses_value: "До 7%"
						}
					],
					short_desc: '(Описание бонуса) 4 bonuses up to €150 Terms & Conditions 18+. ' +
					'First 4 deposits of €10+. Certain deposit methods excluded.',
					licensed: [
						'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/krail_45.png',
						'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/curacao_45.png'
					],
					permalink: '/casino/link-3'
				},
				{
					title: '777 Original Обзор',
					ref: ['/ref-1', '/ref-2'],
					thumbnail: '/img/casino-logo.png',
					bonuses: [
						{
							bonuses_title: "Приветственный пакет",
							bonuses_sub_title: "Вейджер x40",
							bonuses_value: "24000 ₴ + 225FS"
						},
						{
							bonuses_title: "Кэшбэк от ваших ставок",
							bonuses_sub_title: "Зависит от VIP-статуса",
							bonuses_value: "До 7%"
						},
						{
							bonuses_title: "Вейджер",
							bonuses_sub_title: "Обмен CP на деньги",
							bonuses_value: "До 7%"
						}
					],
					short_desc: '(Описание бонуса) 4 bonuses up to €150 Terms & Conditions 18+. ' +
					'First 4 deposits of €10+. Certain deposit methods excluded.',
					licensed: [
						'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/krail_45.png',
						'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/curacao_45.png'
					],
					permalink: '/casino/link-3'
				},
				{
					title: '777 Original Обзор',
					ref: ['/ref-1', '/ref-2'],
					thumbnail: '/img/casino-logo.png',
					bonuses: [
						{
							bonuses_title: "Приветственный пакет",
							bonuses_sub_title: "Вейджер x40",
							bonuses_value: "24000 ₴ + 225FS"
						},
						{
							bonuses_title: "Кэшбэк от ваших ставок",
							bonuses_sub_title: "Зависит от VIP-статуса",
							bonuses_value: "До 7%"
						},
						{
							bonuses_title: "Вейджер",
							bonuses_sub_title: "Обмен CP на деньги",
							bonuses_value: "До 7%"
						}
					],
					short_desc: '(Описание бонуса) 4 bonuses up to €150 Terms & Conditions 18+. ' +
					'First 4 deposits of €10+. Certain deposit methods excluded.',
					licensed: [
						'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/krail_45.png',
						'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/curacao_45.png'
					],
					permalink: '/casino/link-3'
				},
				{
					title: '777 Original Обзор',
					ref: ['/ref-1', '/ref-2'],
					thumbnail: '/img/casino-logo.png',
					bonuses: [
						{
							bonuses_title: "Приветственный пакет",
							bonuses_sub_title: "Вейджер x40",
							bonuses_value: "24000 ₴ + 225FS"
						},
						{
							bonuses_title: "Кэшбэк от ваших ставок",
							bonuses_sub_title: "Зависит от VIP-статуса",
							bonuses_value: "До 7%"
						},
						{
							bonuses_title: "Вейджер",
							bonuses_sub_title: "Обмен CP на деньги",
							bonuses_value: "До 7%"
						}
					],
					short_desc: '(Описание бонуса) 4 bonuses up to €150 Terms & Conditions 18+. ' +
					'First 4 deposits of €10+. Certain deposit methods excluded.',
					licensed: [
						'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/krail_45.png',
						'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/curacao_45.png'
					],
					permalink: '/casino/link-3'
				},
				{
					title: '777 Original Обзор',
					ref: ['/ref-1', '/ref-2'],
					thumbnail: '/img/casino-logo.png',
					bonuses: [
						{
							bonuses_title: "Приветственный пакет",
							bonuses_sub_title: "Вейджер x40",
							bonuses_value: "24000 ₴ + 225FS"
						},
						{
							bonuses_title: "Кэшбэк от ваших ставок",
							bonuses_sub_title: "Зависит от VIP-статуса",
							bonuses_value: "До 7%"
						},
						{
							bonuses_title: "Вейджер",
							bonuses_sub_title: "Обмен CP на деньги",
							bonuses_value: "До 7%"
						}
					],
					short_desc: '(Описание бонуса) 4 bonuses up to €150 Terms & Conditions 18+. ' +
					'First 4 deposits of €10+. Certain deposit methods excluded.',
					licensed: [
						'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/krail_45.png',
						'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/curacao_45.png'
					],
					permalink: '/casino/link-3'
				}
			],
            bonuses: [
                {
                	title: 'Slotoking Обзор',
                    thumbnail: '/img/casino-logo.png',
                    sub_title: 'Приветственный пакет',
                    value: '24 000 ₴ + 225FS',
                    short_desc: '(Описание бонуса) 4 bonuses up to €150 Terms & Conditions 18+. ' +
                    'First 4 deposits of €10+. Certain deposit methods excluded. ' +
                    '4 bonuses available in chronological order. 40x playthrough within 14 days.',
                    ref: ['link-1', 'link-2']
                },
				{
					title: 'Slotoking Обзор',
					thumbnail: '/img/casino-logo.png',
					sub_title: 'Приветственный пакет',
					value: '24 000 ₴ + 225FS',
					short_desc: '(Описание бонуса) 4 bonuses up to €150 Terms & Conditions 18+. ' +
					'First 4 deposits of €10+. Certain deposit methods excluded. ' +
					'4 bonuses available in chronological order. 40x playthrough within 14 days.',
					ref: ['link-1', 'link-2']
				},
				{
					title: 'Slotoking Обзор',
					thumbnail: '/img/casino-logo.png',
					sub_title: 'Приветственный пакет',
					value: '24 000 ₴ + 225FS',
					short_desc: '(Описание бонуса) 4 bonuses up to €150 Terms & Conditions 18+. ' +
					'First 4 deposits of €10+. Certain deposit methods excluded. ' +
					'4 bonuses available in chronological order. 40x playthrough within 14 days.',
					ref: ['link-1', 'link-2']
				},
				{
					title: 'Slotoking Обзор',
					thumbnail: '/img/casino-logo.png',
					sub_title: 'Приветственный пакет',
					value: '24 000 ₴ + 225FS',
					short_desc: '(Описание бонуса) 4 bonuses up to €150 Terms & Conditions 18+. ' +
					'First 4 deposits of €10+. Certain deposit methods excluded. ' +
					'4 bonuses available in chronological order. 40x playthrough within 14 days.',
					ref: ['link-1', 'link-2']
				}

            ],
            top_casinos: [
			{
				title: '777 Original Обзор',
				ref: ['/ref-1', '/ref-2'],
				thumbnail: '/img/casino-logo.png',
				bonuses: [
					{
						bonuses_title: "Приветственный пакет",
						bonuses_sub_title: "Вейджер x40",
						bonuses_value: "24000 ₴ + 225FS"
					},
					{
						bonuses_title: "ТУРНИР-МАРАФОН",
						bonuses_sub_title: "Зависит от VIP-статуса",
						bonuses_value: "50 000 ₽"
					},
					{
						bonuses_title: "Вейджер",
						bonuses_sub_title: "Обмен CP на деньги",
						bonuses_value: "x30"
					}
				],
				short_desc: '(Описание бонуса) 4 bonuses up to €150 Terms & Conditions 18+. ' +
				'First 4 deposits of €10+. Certain deposit methods excluded.',
				licensed: [
					'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/krail_45.png',
					'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/curacao_45.png'
				],
				permalink: '/casino/link-1'
			},
			{
				title: '777 Original Обзор',
				ref: ['/ref-1', '/ref-2'],
				thumbnail: '/img/casino-logo.png',
				bonuses: [
					{
						bonuses_title: "Приветственный пакет",
						bonuses_sub_title: "Вейджер x40",
						bonuses_value: "24000 ₴ + 225FS"
					},
					{
						bonuses_title: "БОНУС \"WEDNESDAY\"",
						bonuses_sub_title: "Зависит от VIP-статуса",
						bonuses_value: "До 7%"
					},
					{
						bonuses_title: "Вейджер",
						bonuses_sub_title: "Обмен CP на деньги",
						bonuses_value: "x40"
					}
				],
				short_desc: '(Описание бонуса) 4 bonuses up to €150 Terms & Conditions 18+. ' +
				'First 4 deposits of €10+. Certain deposit methods excluded.',
				licensed: [],
				permalink: '/casino/link-2'
			},
			{
				title: '777 Original Обзор',
				ref: ['/ref-1', '/ref-2'],
				thumbnail: '/img/casino-logo.png',
				bonuses: [
					{
						bonuses_title: "Приветственный пакет",
						bonuses_sub_title: "Вейджер x40",
						bonuses_value: "24000 ₴ + 225FS"
					},
					{
						bonuses_title: "Кэшбэк от ваших ставок",
						bonuses_sub_title: "Зависит от VIP-статуса",
						bonuses_value: "До 7%"
					},
					{
						bonuses_title: "Вейджер",
						bonuses_sub_title: "Обмен CP на деньги",
						bonuses_value: "До 7%"
					}
				],
				short_desc: '(Описание бонуса) 4 bonuses up to €150 Terms & Conditions 18+. ' +
				'First 4 deposits of €10+. Certain deposit methods excluded.',
				licensed: [
					'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/krail_45.png',
					'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/curacao_45.png'
				],
				permalink: '/casino/link-3'
			},
			{
				title: '777 Original Обзор',
				ref: ['/ref-1', '/ref-2'],
				thumbnail: '/img/casino-logo.png',
				bonuses: [
					{
						bonuses_title: "Приветственный пакет",
						bonuses_sub_title: "Вейджер x40",
						bonuses_value: "24000 ₴ + 225FS"
					},
					{
						bonuses_title: "Кэшбэк от ваших ставок",
						bonuses_sub_title: "Зависит от VIP-статуса",
						bonuses_value: "До 7%"
					},
					{
						bonuses_title: "Вейджер",
						bonuses_sub_title: "Обмен CP на деньги",
						bonuses_value: "До 7%"
					}
				],
				short_desc: '(Описание бонуса) 4 bonuses up to €150 Terms & Conditions 18+. ' +
				'First 4 deposits of €10+. Certain deposit methods excluded.',
				licensed: [
					'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/krail_45.png',
					'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/curacao_45.png'
				],
				permalink: '/casino/link-3'
			},
			{
				title: '777 Original Обзор',
				ref: ['/ref-1', '/ref-2'],
				thumbnail: '/img/casino-logo.png',
				bonuses: [
					{
						bonuses_title: "Приветственный пакет",
						bonuses_sub_title: "Вейджер x40",
						bonuses_value: "24000 ₴ + 225FS"
					},
					{
						bonuses_title: "Кэшбэк от ваших ставок",
						bonuses_sub_title: "Зависит от VIP-статуса",
						bonuses_value: "До 7%"
					},
					{
						bonuses_title: "Вейджер",
						bonuses_sub_title: "Обмен CP на деньги",
						bonuses_value: "До 7%"
					}
				],
				short_desc: '(Описание бонуса) 4 bonuses up to €150 Terms & Conditions 18+. ' +
				'First 4 deposits of €10+. Certain deposit methods excluded.',
				licensed: [
					'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/krail_45.png',
					'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/curacao_45.png'
				],
				permalink: '/casino/link-3'
			},
			{
				title: '777 Original Обзор',
				ref: ['/ref-1', '/ref-2'],
				thumbnail: '/img/casino-logo.png',
				bonuses: [
					{
						bonuses_title: "Приветственный пакет",
						bonuses_sub_title: "Вейджер x40",
						bonuses_value: "24000 ₴ + 225FS"
					},
					{
						bonuses_title: "Кэшбэк от ваших ставок",
						bonuses_sub_title: "Зависит от VIP-статуса",
						bonuses_value: "До 7%"
					},
					{
						bonuses_title: "Вейджер",
						bonuses_sub_title: "Обмен CP на деньги",
						bonuses_value: "До 7%"
					}
				],
				short_desc: '(Описание бонуса) 4 bonuses up to €150 Terms & Conditions 18+. ' +
				'First 4 deposits of €10+. Certain deposit methods excluded.',
				licensed: [
					'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/krail_45.png',
					'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/curacao_45.png'
				],
				permalink: '/casino/link-3'
			},
			{
				title: '777 Original Обзор',
				ref: ['/ref-1', '/ref-2'],
				thumbnail: '/img/casino-logo.png',
				bonuses: [
					{
						bonuses_title: "Приветственный пакет",
						bonuses_sub_title: "Вейджер x40",
						bonuses_value: "24000 ₴ + 225FS"
					},
					{
						bonuses_title: "Кэшбэк от ваших ставок",
						bonuses_sub_title: "Зависит от VIP-статуса",
						bonuses_value: "До 7%"
					},
					{
						bonuses_title: "Вейджер",
						bonuses_sub_title: "Обмен CP на деньги",
						bonuses_value: "До 7%"
					}
				],
				short_desc: '(Описание бонуса) 4 bonuses up to €150 Terms & Conditions 18+. ' +
				'First 4 deposits of €10+. Certain deposit methods excluded.',
				licensed: [
					'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/krail_45.png',
					'https://media.onlinecasino.kyiv.ua/wp-content/uploads/2021/07/curacao_45.png'
				],
				permalink: '/casino/link-3'
			}
		],
        }
    },
    components: {app_content, app_casino_loop, app_banner, app_blog_card, app_top_bonuses},
    async asyncData({store, route}) {
        const request = {
            type: 'page',
            url: '/'
        }
        const response = await DAL_Page.getData(request)
        const body = response.data  
        const data = body
        data.body.currentUrl = config.BASE_URL
        return {data}
    },
    head() {
        return {
            title: this.data.body.meta_title,
            meta: [
                {
                    hid: 'description',
                    name: 'description',
                    content: this.data.body.meta_description
                },
                {
                    hid: 'classification',
                    name: 'classification',
                    content: this.data.body.meta.classification
                },
                {
                    hid: 'distribution',
                    name: 'distribution',
                    content: this.data.body.meta.distribution
                },
                {
                    hid: 'author',
                    name: 'author',
                    content: this.data.body.meta.author
                },
                {
                    hid: 'creator',
                    name: 'creator',
                    content: this.data.body.meta.creator
                },
                {
                    hid: 'copyright',
                    name: 'copyright',
                    content: this.data.body.meta.copyright
                },
                {
                    hid: 'publisher',
                    name: 'publisher',
                    content: this.data.body.meta.publisher
                },
                {
                    hid: 'geo.placename',
                    name: 'geo.placename',
                    content: this.data.body.meta.placename
                },
                {
                    hid: 'geo.position',
                    name: 'geo.position',
                    content: this.data.body.meta.position
                },
                {
                    hid: 'geo.region',
                    name: 'geo.region',
                    content: this.data.body.meta.region
                },
                {
                    hid: 'ICBM',
                    name: 'ICBM',
                    content: this.data.body.meta.ICBM
                },
                {
                    hid: 'robots',
                    name: 'robots',
                    content: this.data.body.meta.robots
                },
               // og //
                {
                    hid: 'og:locale',
                    property: 'og:locale',
                    content: 'ru-UA'
                },
                {
                    hid: 'og:type',
                    property: 'og:type',
                    content: 'website'
                },
                {
                    hid: 'og:title',
                    property: 'og:title',
                    content: this.data.body.meta_title
                },
                {
                    hid: 'og:description',
                    property: 'og:description',
                    content: this.data.body.meta_description
                },
                {
                    hid: 'og:url',
                    property: 'og:url',
                    content: this.data.body.currentUrl,
                },
                {
                    hid: 'og:article:section',
                    property: 'og:article:section',
                    content: this.data.body.h1,
                },
                {
                    hid: 'og:article:published_time',
                    property: 'og:article:published_time',
                    content: this.data.body.date,
                },
                {
                    hid: 'og:article:modified_time',
                    property: 'og:article:modified_time',
                    content: this.data.body.date_modified,
                },
                {
                    hid: 'og:image',
                    property: 'og:image',
                    content: this.data.body.thumbnail,
                },
                // end og //
                // twitter //
                {
                    hid: 'twitter:card',
                    name: 'twitter:card',
                    content: 'summary'
                },
                {
                    hid: 'twitter:title',
                    name: 'twitter:title',
                    content: this.data.body.meta_title,
                },
                {
                    hid: 'twitter:description',
                    name: 'twitter:description',
                    content: this.data.body.meta_description,
                },
                {
                    hid: 'twitter:image',
                    name: 'twitter:image',
                    content: this.data.body.thumbnail,
                },
                {
                    hid: 'twitter:url',
                    name: 'twitter:url',
                    content: this.data.body.currentUrl,
                },
                // end twitter //

            ],
            link: [
                { rel: 'canonical', href: this.data.body.currentUrl}
            ]
        }
    }
}
</script>

<style>

</style>
