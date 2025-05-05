<template>
  <div>
    <header class="header">
      <div class="header__top">
        <div class="header__contact">
          <img src="@/assets/img/geo.png" alt="geo" style="margin-right: 8px" />
          Сайлент-Хилл
          <img
            src="@/assets/img/phone.png"
            alt="phone"
            style="margin-right: 8px"
          />тел: 09547823742
        </div>
        <div class="header__work-time">Ежедневно 9:00 - 21:00</div>
        <div class="header__details">
          <a href="#" class="header__detail">Доставка</a>
          <a href="#" class="header__detail">Оплата</a>
          <a href="#" class="header__detail">Контакты</a>
        </div>
      </div>

      <div class="header__block">
        <div class="header__logo">
          <a href="index.html">
            <img src="@/assets/img/logo.png" alt="Logo" />
          </a>
        </div>

        <div class="header__center">
          <div class="header__top-row">
            <div class="header__burger-menu" ref="menuWrapper">
              <BurgerMenuComp
                @toggle-menu="openMenu"
                :menuIsOpen="menuIsOpen"
              />
            </div>

            <div class="header__search">
              <input
                class="header__input"
                type="text"
                placeholder="Поиск товаров..."
              />
              <div class="header__button-search">Найти</div>
            </div>

            <div class="header__messengers">
              <a
                href="https://web.telegram.org/a/"
                target="_blank"
                rel="noopener noreferrer"
                ><img
                  class="header__messenger-icon"
                  src="@/assets/img/1.svg"
                  alt="Telegram"
              /></a>
              <a
                href="https://web.whatsapp.com"
                target="_blank"
                rel="noopener noreferrer"
                ><img
                  class="header__messenger-icon"
                  src="@/assets/img/2.svg"
                  alt="WhatsApp"
              /></a>
            </div>
          </div>

          <div class="header__bottom-row" @mouseleave="hoveredEvent = null">
            <div class="header__buttons">
              <button
                class="header__button"
                
                @mouseenter="menuIsOpen ? null : handleMouseEnter('promotion')"
              >
                <img src="@/assets/img/fire.png" alt="promotion" />
                Акция
                <div v-if="hoveredEvent === 'promotion'" class="tooltip">
                  <ToolTipsComp :hoveredEvent="hoveredEvent" />
                </div>
              </button>

              <button
                class="header__button"
                @mouseenter="hoveredEvent = 'offer'"
              >
                <img src="@/assets/img/lightning.png" alt="sale" />
                Горячее предложение
                <div v-if="hoveredEvent === 'offer'" class="tooltip">
                  <ToolTipsComp :hoveredEvent="hoveredEvent" />
                </div>
              </button>

              <button
                class="header__button"
                @mouseenter="hoveredEvent = 'gifts'"
              >
                <img src="@/assets/img/fire.png" alt="gifts" />
                Подарочные наборы
                <div v-if="hoveredEvent === 'gifts'" class="tooltip">
                  <ToolTipsComp :hoveredEvent="hoveredEvent" />
                </div>
              </button>

              <button
                class="header__button"
                @mouseenter="hoveredEvent = 'action'"
              >
                <img src="@/assets/img/fire.png" alt="action" />
                События
                <div v-if="hoveredEvent === 'action'" class="tooltip">
                  <ToolTipsComp :hoveredEvent="hoveredEvent" />
                </div>
              </button>

              <button
                class="header__button"
                @mouseenter="hoveredEvent = 'brends'"
              >
                <img src="@/assets/img/orc.png" alt="brends" />
                Наши бренды
                <div v-if="hoveredEvent === 'brends'" class="tooltip">
                  <ToolTipsComp :hoveredEvent="hoveredEvent" />
                </div>
              </button>
            </div>
          </div>
        </div>

        <div class="header__lang">
          <img src="@/assets/img/world.png" alt="lang" />RU|EN
        </div>

        <div class="header__right">
          <div class="header__icons">
            <div class="header__icon">
              <img src="@/assets/img/heart.png" alt="like" />
            </div>
            <div class="header__icon">
              <img src="@/assets/img/hunter.png" alt="hunter" />
            </div>
            <div class="header__icon">
              <img src="@/assets/img/chest.png" alt="chest" />
            </div>
          </div>

          <div class="header__assemble">+ Собрать компьютер</div>
        </div>
      </div>
    </header>
  </div>
</template>

<script>
import BurgerMenuComp from "./BurgerMenuComp.vue";
import ToolTipsComp from "./ToolTipsComp.vue";

export default {
  data() {
    return {
      menuIsOpen: false,
      hoveredEvent: null,
    };
  },
  methods: {
    openMenu() {
      this.menuIsOpen = !this.menuIsOpen;
    },
    // handleClickOutside(event) {

    //     this.hoveredEvent = event;

    // },
    handleMouseEnter(action) {
    
    this.hoveredEvent = action;
  },
  },
  mounted() {
    document.addEventListener("click", this.handleClickOutside);
  },
  beforeUnmount() {
    document.removeEventListener("click", this.handleClickOutside);
  },
  components: {
    BurgerMenuComp,
    ToolTipsComp,
  },
  watch: {
    menuIsOpen(newValue) {
      if (newValue === true) {
        this.hoveredEvent = null;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.header {
  display: flex;
  flex-direction: column;
  width: 100%;

  &__top {
    display: flex;
    justify-content: space-between;
    background: #f4f4f4;
    padding: 6px;
  }

  &__details {
    display: flex;
    gap: 16px;
  }

  &__detail:hover {
    color: #4888ff;
  }

  &__block {
    display: flex;
    justify-content: space-between;
    margin-top: 16px;
    gap: 8px;
  }

  &__top-row {
    display: flex;
    gap: 16px;
  }

  &__button-search {
    padding: 0 12px;
    height: 40px;
    border-radius: 4px;
    background: #4888ff;
    color: #ffffff;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    font-size: 0.9rem;
  }

  &__search {
    flex: 1;
    min-width: 200px;
    display: flex;
    align-items: center;
    border-radius: 8px;
    border: 1px solid rgba(72, 136, 255, 0.2);
    padding-right: 4px;
    background: #fff;
  }

  &__input {
    flex: 1;
    height: 100%;
    padding-left: 12px;
    border: none;
    outline: none;
    font-size: 1rem;
  }

  &__bottom-row {
    padding: 8px;
  }

  &__buttons {
    display: flex;
    justify-content: space-between;
    margin-top: 20px;
    gap: 8px;
  }

  &__button,
  &__assemble {
    height: 42px;
    padding-top: 11px;
    padding-right: 16px;
    padding-bottom: 11px;
    padding-left: 16px;
    border-radius: 8px;
    background: #f4f4f4;
    border: none;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 10px;
    cursor: pointer;
    text-align: center;
    position: relative;
  }

  &__button:hover {
    color: #4888ff;
  }

  &__messengers {
    display: flex;
    gap: 6px;
  }

  &__messenger-icon {
    width: 48px;
    background: #f4f4f4;
    border-radius: 4px;
    padding: 12px;
  }

  &__lang {
    display: flex;
    gap: 6px;
    align-items: flex-start;
    padding-top: 16px;
    cursor: pointer;
  }

  &__icons {
    display: flex;
    justify-content: space-between;
    gap: 6px;
  }

  &__icon {
    border: 1px solid #d3d3d3;
    width: 48px;
    height: 48px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    border-radius: 4px;
  }

  &__icon:hover {
    background: #d4d9dd;
    border: 2px solid #4888ff;
  }

  &__assemble {
    color: #4888ff;
  }

  &__assemble:hover {
    background-color: #4888ff;
    color: #ffffff;
  }

  &__right {
    display: flex;
    flex-direction: column;
    gap: 20px;
  }
}

.header__messenger-icon:hover {
  background: #d4d9dd;
  border: 2px solid #4888ff;
}

.tooltip {
  position: absolute;
  top: 100%;
  left: 0;
  z-index: 10;
  background-color: white;
  border: 1px solid #d3d3d3;
  padding: 12px;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}
</style>
