<template>
  <div v-if="hoveredEvent === 'promotion'">
    Здесь будут отображаться наши акции
  </div>

  <div v-if="hoveredEvent === 'offer'">
    Здесь будут отображаться наши предложения
  </div>

  <div v-if="hoveredEvent === 'gifts'">
    <MenuItem
      :items="menuGifts"
      customClass="my-gift-menu"
      :customStyle="{ position: 'absolute',top:'0', width:'200px', left:'0'}"
    />
  </div>

  <div v-if="hoveredEvent === 'action'">
    <div class="toolTipsBox">
      <a href="#">ИгроМИР</a>
      <a href="#">Мероприятия</a>
      <a href="#">Мастер-классы</a>
    </div>
  </div>

  <div v-if="hoveredEvent === 'brends'">
    <h3>Наши бренды:</h3>
    <ul>
      <li><a href="#">Бренд 1</a></li>
      <li><a href="#">Бренд 2</a></li>
      <li><a href="#">Бренд 3</a></li>
    </ul>
  </div>
</template>

<script>
import MenuItem from "./MenuItem.vue";

export default {
  props: {
    hoveredEvent: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      menuGifts: [
        {
          title: "Кому",
          image: "",
          subsections: [
            {
              category: "Кому?",
              items: [
                { name: "Для мужчин" },
                { name: "Для женщин" },
                { name: "Папе" },
                { name: "Сотрудникам" },
                { name: "Мужу" },
                { name: "Корпоративный" },
              ],
            },
          ],
        },
        {
          title: "Повод",
          image: "",
          subsections: [
            {
              category: "Повод",
              items: [
                { name: "День рождения" },
                { name: "Новый год" },
                { name: "8 марта" },
                { name: "23 февраля" },
              ],
            },
          ],
        },
        {
          title: "Наполнение",
          image: "",
          subsections: [
            {
              category: "Наполнение",
              items: [
                { name: "Сладкий подарок" },
                { name: "Впечатления" },
                { name: "На память" },
              ],
            },
          ],
        },
      ],
    };
  },
  components: {
    MenuItem,
  },
};
</script>

<style lang="scss" scoped>
.toolTipsBox {
    min-width: 150px;
  display: flex;
  gap: 16px;
  flex-direction: column;
  align-items: center;
}
h3{
    margin-bottom: 16px;
}
</style>
