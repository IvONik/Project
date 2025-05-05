<template>
  
    <div class="menu-container">
    <div @click="toggleMenu">
      <img src="@/assets/img/Frame6.png" alt="Menu" />
    </div>
    
    <div v-if="menuIsOpen" class="menu">
      <MenuItem :items="menuData" customClass="my-gift-menu"
      :customStyle="{ position: 'absolute', top: '130px', right: '-250px' }"/>
    </div>
  
</div>
  
</template>

<script>
import MenuItem from "./MenuItem.vue";
import iconphone from "@/assets/img/phone2.png";
import iconTV from "@/assets/img/tv.png";
import iconaudio from "@/assets/img/audio.png";
import iconLaptop from "@/assets/img/laptop.png";
import iconNew from "@/assets/img/laptop.png";
import iconPromotion from "@/assets/img/fire.png";

export default {
  components: { MenuItem },
  data() {
    return {
      menuIsOpen: false,
      menuData: [
        {
          title: "Смартфоны и гаджеты",
          image: iconphone,
          subsections: [
            {
              category: "Смартфоны",
              items: [
                { name: "Apple iPhone", count: 123 },
                { name: "iPhone 15", count: 120 },
                { name: "Foldables", count: 3 },
                { name: "realme", count: 22 },
                { name: "Huawei Mate X6", count: 10 },
                { name: "Concept Phones", count: 23 },
                { name: "Home Devices", count: 11 },
                { name: "Samsung", count: 27 },
              ],
            },
            {
              category: "Гаджеты",
              items: [
                { name: "Smartwatches", count: 15 },
                { name: "Smart Rings", count: 34 },
                { name: "Headphones", count: 21 },
                { name: "Headsets", count: 1 },
                { name: "Portable Audio", count: 42 },
                { name: "Smart Gadgets", count: 45 },
                { name: "VR Glasses", count: 12 },
                { name: "For Bloggers", count: 3 },
              ],
            },
          ],
        },
        {
          title: "Ноутбуки и компьютеры",
          image: iconLaptop,
          subsections: [
            {
              category: "Ноутбуки",
              items: [
                { name: "Apple iPhone", count: 123 },
                { name: "iPhone 15", count: 120 },
                { name: "Foldables", count: 3 },
                { name: "realme", count: 22 },
                { name: "Huawei Mate X6", count: 10 },
                { name: "Concept Phones", count: 23 },
                { name: "Home Devices", count: 11 },
                { name: "Samsung", count: 27 },
              ],
            },
            {
              category: "Компьютеры",
              items: [
                { name: "Smartwatches", count: 15 },
                { name: "Smart Rings", count: 34 },
                { name: "Headphones", count: 21 },
                { name: "Headsets", count: 12 },
                { name: "Portable Audio", count: 42 },
                { name: "Smart Gadgets", count: 45 },
                { name: "VR Glasses", count: 49 },
                { name: "For Bloggers", count: 32 },
              ],
            },
          ],
        },
        {
          title: "Телевизоры и цифровое ТВ",
          image: iconTV,
          items: [
            { name: "Smartwatches", count: 15 },
            { name: "Smart Rings", count: 34 },
            { name: "Headphones", count: 21 },
            { name: "Headsets", count: 12 },
            { name: "Portable Audio", count: 42 },
            { name: "Smart Gadgets", count: 45 },
            { name: "VR Glasses", count: 49 },
            { name: "For Bloggers", count: 32 },
          ],
        },
        {
          title: "Аудиотехника",
          image: iconaudio,
        },
        {
          title: "Акции",
          image: iconPromotion,
        },
        {
          title: "Новинки",
          image: iconNew,
        },
      ],
    };
  },
  methods: {
    toggleMenu() {
      this.menuIsOpen = !this.menuIsOpen;
    },
  },
};
</script>

<style scoped>

.menu-container {
  width: 101px;
  height: 48px;
  border-radius: 8px;
  background: #4888ff;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  position: relative;
  z-index: 10;
}
</style>
