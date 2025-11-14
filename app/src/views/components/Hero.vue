<template>
  <section class="hero-section py-5">
    <div class="container">
      <!-- ドロップダウン右寄せ -->
      <div
        class="d-flex justify-content-end mb-3 position-relative"
        style="width: 100%"
      >
        <div class="relative w-[156px]">
          <button
            class="btn btn-outline-secondary"
            @click="toggleDropdown"
            :aria-expanded="dropdownOpen.toString()"
          >
            <span class="truncate">{{ selectedOption }}</span>
            <svg
              width="20"
              height="20"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
              class="pointer-events-none"
            >
              <polyline points="6 9 12 15 18 9"></polyline>
            </svg>
          </button>
          <ul v-show="dropdownOpen" class="dropdown-menu-right">
            <li
              v-for="(option, index) in sortOptions"
              :key="index"
              @click="selectOption(option)"
            >
              {{ option }}
            </li>
          </ul>
        </div>
      </div>

      <!-- 画像群 -->
      <div class="image-group d-flex flex-wrap gap-3">
        <a
          v-for="(item, i) in selectedSiteTypes"
          :key="i"
          :href="item.url"
          target="_blank"
          class="card card-link"
        >
          <img :src="item.img" class="card-img-top" alt="" />
          <div class="card-body text-center">
            <small>{{ item.name }}</small>
          </div>
        </a>
      </div>
    </div>
  </section>
</template>

<script>
import siteTypes from "@/data/siteTypes.json";
export default {
  data() {
    return {
      dropdownOpen: false,
      sortOptions: ["人気順", "新着順", "おすすめ"], // 表示ラベル
      selectedOption: "人気順",
      allSiteTypes: siteTypes,
      sortMap: {
        人気順: "popular",
        新着順: "new",
        おすすめ: "recommended",
      },
    };
  },
  computed: {
    selectedSiteTypes() {
      const key = this.sortMap[this.selectedOption];
      return this.allSiteTypes[key] || [];
    },
  },
  methods: {
    toggleDropdown() {
      this.dropdownOpen = !this.dropdownOpen;
    },
    selectOption(option) {
      this.selectedOption = option;
      this.dropdownOpen = false;
    },
  },
};
</script>

<style scoped>
.hero-section {
  padding-top: 40px;
  padding-bottom: 40px;
}

.container {
  max-width: 1040px;
  margin: 0 auto;
  padding-left: 16px;
  padding-right: 16px;
}

.dropdown-menu-right {
  position: absolute;
  top: 100%;
  right: 0;
  margin: 12px 0px;
  background-color: #fff;
  border: 1px solid #d1d5db;
  border-radius: 6px;
  min-width: 156px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  z-index: 20;
  list-style: none;
  padding: 0;
}

.dropdown-menu-right li {
  padding: 8px 12px;
  cursor: pointer;
  font-size: 14px;
}

.dropdown-menu-right li:hover {
  background-color: #f3f4f6;
}

/* 画像群 */
.image-group {
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
}

.image-group .card-link {
  width: calc((100% - 16px * 3) / 4); /* 4列表示、gapを3回分引く */
  cursor: pointer;
  transition: transform 0.2s, box-shadow 0.2s;
  margin-left: 0px;
}

.image-group .card-link:hover {
  transform: translateY(-3px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.image-group .card img {
  object-fit: cover;
  height: 180px;
  width: 100%;
}

.image-group .card-body small {
  display: block;
  font-size: 12px;
  text-align: center;
}
</style>
