<template>
  <div class="menu-box"
  :class="customClass"
  :style="customStyle">
    <div
      class="menu-layout"
      @mouseleave="hoveredIndex = null"
    >
      <!-- Главное меню -->
      <ul class="menu-list">
        <li
          v-for="(item, index) in items"
          :key="index"
          class="menu-item"
          @mouseenter="hoveredIndex = index"
        >
          <div class="menu-title">
            <img v-if="item.image" :src="item.image" alt="" class="menu-icon" />
            <span>{{ item.title || item.category || item.name }}</span>
            <span v-if="item.count">({{ item.count }})</span>
            <div v-if="item.subsections || item.items" class="title-arrow">
              <img src="@/assets/img/right.png" alt="arrow" />
            </div>
          </div>
        </li>
      </ul>

      <!-- Подменю -->
      <div
        class="submenu-area"
        v-if="currentItemHasSubmenu"
      >
        <div v-if="currentItem.subsections" class="submenu two-columns">
          <div
            class="submenu-column"
            v-for="(section, secIndex) in currentItem.subsections"
            :key="secIndex"
          >
            <h4 class="submenu-header">{{ section.category }}</h4>
            <ul class="submenu-items">
              <li
                v-for="(subItem, subIndex) in section.items"
                :key="subIndex"
                class="submenu-item"
              >
                {{ subItem.name }}
                <span class="count">{{ subItem.count }}</span>
              </li>
            </ul>
          </div>
        </div>

        <div v-else-if="currentItem.items" class="submenu">
          <ul class="submenu-items">
            <li
              v-for="(subItem, subIndex) in currentItem.items"
              :key="subIndex"
              class="submenu-item"
            >
              {{ subItem.name }}
              <span >{{ subItem.count }}</span>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MenuItem",
  props: {
    items: {
    type: Array,
    required: true
  },
  customClass: {
    type: String,
    default: ''
  },
  customStyle: {
    type: Object,
    default: () => ({})
  }
  },
  data() {
    return {
      hoveredIndex: null,
    };
  },
  computed: {
    currentItem() {
      return this.items[this.hoveredIndex];
    },
    currentItemHasSubmenu() {
      const item = this.currentItem;
      return item && (item.subsections || item.items);
    },
  },
};
</script>

<style scoped>
.menu-box {
  /* position: absolute;
  top: 130px;
  right: -250px; */
  z-index: 999;
}

.menu-layout {
  display: flex;
  flex-direction: row;
  background-color: #fff;
  border-radius: 12px 0 0 12px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
  padding: 20px;
  min-width: 200px;
}

.menu-list {
  list-style: none;
  padding: 0 16px 0 0;
  margin: 0;
  width: 300px;
  display: flex;
  flex-direction: column;
  gap: 8px;
  border-bottom: 1px solid #eee;
}

.menu-item {
  cursor: pointer;
  padding: 8px;
  border-radius: 4px;
  border-bottom: 1px solid #eee;
}

.menu-item:hover {
  background-color: #f3f6fd;
}

.menu-title {
  display: flex;
  align-items: center;
  gap: 8px;
  position: relative;
}

.menu-icon {
  width: 16px;
  height: 16px;
}

.title-arrow {
  margin-left: auto;
}

.submenu-area {
  position: absolute;
  top:0;
  left: 100%;
  padding-left: 20px;
  min-width: 300px;
  display: flex;
  flex-direction: column;
  background-color: #fff;
  border-radius: 0 12px 12px 0;
  padding: 20px;
  min-width: 300px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);

}

.submenu {
  display: flex;
  gap: 40px;
}

.submenu-column {
  display: flex;
  flex-direction: column;
}

.submenu-header {
  font-weight: 600;
  margin-bottom: 16px;
}

.submenu-items {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.submenu-item {
  font-size: 14px;
  margin-bottom: 6px;
  display: flex;
  color: #333;
  gap: 8px;
}
.submenu-item:hover,
.count:hover{
  color: #4888FF;

}

.submenu-icon {
  width: 16px;
  height: 16px;
  margin-right: 8px;
}

.count {
  color: #999;
  font-size: 13px;
}

</style>
