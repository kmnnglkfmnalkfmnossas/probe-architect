<script setup>
import { inject, onMounted } from 'vue'

import { dialog } from '../utils'

// eslint-disable-next-line no-unused-vars
const translate = inject('translate')
// eslint-disable-next-line no-unused-vars
const log = inject('log')
// eslint-disable-next-line no-unused-vars
const media = inject('media')

const emit = defineEmits(['next'])

onMounted(() => {
  dialog()
})

function next_block(e) {
  e.preventDefault()
  log('ACTIVITY', 'user_finished_block', 5)
  if (window.localStorage.getItem('error') === null) {
    log('ROI', 'user_without_mistake', 5)
  } else {
    log('ROI', 'user_mistake', 5)
    window.localStorage.removeItem('error')
  }
}
</script>

<template>
  <div class="dialog">
    <div class="row justify-content-around dialog_style-1">
      <div class="col-3 dialog_style-2">
        <img
          :src="media('../../public/img/richman.png')"
          alt=""
          class="dialog_style-3"
        />
      </div>
      <div class="col-6 dialog_style-4">
        <div class="stage0 col-stage active">
          <div class="archContainer rounded-all r0 f-speach">
            <b>
              <p>{{ translate('Главный архитектор') }}</p>
            </b>
            <p>{{ translate('Здравствуйте, Дмитрий Иванович!') }}</p>
          </div>
          <div class="richContainer rounded-all r1 f-speach">
            <b>
              <p>{{ translate('Заказчик') }}</p>
            </b>
            <p>
              {{ translate('Добрый день! Ну что, укладываетесь в сроки?') }}
            </p>
          </div>
          <div class="archContainer rounded-all r2 f-speach">
            <b>
              <p>{{ translate('Главный архитектор') }}</p>
            </b>
            <ul>
              <li class="correct" @click="log('ACTIVITY', 'user_action', 4, 1)">
                {{
                  translate(
                    'Конечно, укладываемся. Если сейчас согласуем проект, то уже через две недели закончим с оставшимися расчётами и сможем приступать к строительству.'
                  )
                }}
              </li>
              <li class="wrong" @click="log('ACTIVITY', 'user_action', 4, 2)">
                {{
                  translate(
                    'Э-э… Ну… Знаете, мы ещё не все расчёты провели,топосъёмку не сделали. В общем…'
                  )
                }}
              </li>
            </ul>
          </div>
        </div>

        <div class="stage1 col-stage dialog_style-5">
          <div class="richContainer rounded-all r3">
            <b>
              <p>{{ translate('Заказчик') }}</p>
            </b>
            <p>
              {{
                translate(
                  'Ну, что ж, неплохо. Вижу, и о людях с ограниченными возможностями подумали?'
                )
              }}
            </p>
          </div>
          <div class="archContainer rounded-all r4">
            <b>
              <p>{{ translate('Главный архитектор') }}</p>
            </b>
            <ul>
              <li class="correct" @click="log('ACTIVITY', 'user_action', 4, 3)">
                {{
                  translate(
                    'Да, в местах, где будут уклоны или насыпные возвышенности, мы сделаем удобные дорожки с плавными съездами. В общественных туалетах предусмотрены отдельные комнаты. А все навигационные таблички будем дублировать шрифтом Брайля.'
                  )
                }}
              </li>
              <li class="wrong" @click="log('ACTIVITY', 'user_action', 4, 4)">
                {{
                  translate(
                    'Мы, конечно, подумали, но решили ничего особенного в проект не добавлять.'
                  )
                }}
              </li>
            </ul>
          </div>
        </div>

        <div class="stage2 col-stage dialog_style-6">
          <div class="richContainer rounded-all r5">
            <b>
              <p>{{ translate('Заказчик') }}</p>
            </b>
            <p>{{ translate('А мнение предпринимателей учли?') }}</p>
          </div>
          <div class="archContainer rounded-all r6">
            <b>
              <p>{{ translate('Главный архитектор') }}</p>
            </b>
            <ul>
              <li class="wrong" @click="log('ACTIVITY', 'user_action', 4, 5)">
                {{
                  translate('Зачем? Коммерческие точки появятся сами собой!')
                }}
              </li>
              <li class="correct" @click="log('ACTIVITY', 'user_action', 4, 6)">
                {{
                  translate(
                    'Да, как и обсуждали в самом начале: в парке будут заведения с едой и напитками, ларьки с мороженым и водой, прокат спортивного инвентаря. А на центральной площадке можно будет проводить концерты и выставки.'
                  )
                }}
              </li>
            </ul>
          </div>
        </div>

        <div class="stage3 col-stage dialog_style-7">
          <div class="richContainer rounded-all r7">
            <b>
              <p>{{ translate('Заказчик') }}</p>
            </b>
            <p>
              {{
                translate(
                  'Хорошо. А по объёму расходов мы укладываемся в лимит?'
                )
              }}
            </p>
          </div>
          <div class="archContainer rounded-all r8">
            <b>
              <p>{{ translate('Главный архитектор') }}</p>
            </b>
            <ul>
              <li class="wrong" @click="log('ACTIVITY', 'user_action', 4, 7)">
                {{ translate('Вам денег жалко что ли?') }}
              </li>
              <li class="correct" @click="log('ACTIVITY', 'user_action', 4, 8)">
                {{
                  translate(
                    'Да, сейчас уже понятен предварительный бюджет. Смета рассчитывается в несколько этапов: после проектной стадии и перед стройкой мы ещё раз вместе всё оценим.'
                  )
                }}
              </li>
            </ul>
          </div>
        </div>

        <div class="stage4 col-stage dialog_style-8">
          <div class="richContainer rounded-all r9">
            <b>
              <p>{{ translate('Заказчик') }}</p>
            </b>
            <p>
              {{
                translate(
                  'Тогда всё отлично. Жду оставшуюся документацию. Уверен, парк получится просто прекрасный!'
                )
              }}
            </p>
          </div>
          <div class="archContainer rounded-all r10">
            <b>
              <p>{{ translate('Главный архитектор') }}</p>
            </b>
            <p>{{ translate('Замечательно!') }}</p>
            <div
              @click=";[next_block($event), emit('next')]"
              type="button"
              class="btn btn-outline-warning rounded-all-lightly button-final dialog_style-9"
            >
              <button class="dialog_style-10">
                {{ translate('Закочить переговоры с заказчиком') }}
              </button>
            </div>
          </div>
        </div>
      </div>
      <div class="col-3 dialog_style-11">
        <img
          :src="media('../../public/img/architect.png')"
          class="dialog_style-12"
          alt=""
        />
      </div>
    </div>

    <div class="popup dialog_style-13">
      <div class="popup__icon">
        <img :src="media('../../public/img/icons/attention.svg')" alt="" />
      </div>
      <div class="popup__info">
        <div class="popup__header">
          <h3 class="popup__title">
            {{ translate('Ой, это неверный вариант!') }}
          </h3>
          <button class="popup__close-btn">
            <svg
              width="14"
              height="14"
              viewBox="0 0 14 14"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                fill-rule="evenodd"
                clip-rule="evenodd"
                d="M5.26541 7L0 1.73459L1.73459 0L7 5.26541L12.2654 0L14 1.73459L8.73459 7L14 12.2654L12.2654 14L7 8.73459L1.73459 14L0 12.2654L5.26541 7Z"
                fill="#75797B"
              />
            </svg>
          </button>
        </div>
        <p class="popup__paragraph">
          {{
            translate(
              'Если не знаете, какой вариант выбрать, загляните в справочник.'
            )
          }}
        </p>
      </div>
    </div>
  </div>
</template>
