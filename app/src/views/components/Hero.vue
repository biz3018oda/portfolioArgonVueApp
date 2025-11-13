<template>
  <section class="section-hero section-shaped my-0">
    <div class="row px-4 py-4">
      <!-- 左側ナビ -->
      <div class="col-4">
        <div>
          <h4 class="typography-14-bold color-text px-3 py-1">
            サイト種別から探す
          </h4>

          <nav class="navbar bg-body-tertiary">
            <div class="container-fluid">
              <ul class="navbar-nav flex-column">
                <li class="nav-item" v-for="(item, i) in navItems" :key="i">
                  <a class="nav-link" href="#">
                    <span>{{ item }}</span>
                    <svg
                      width="16"
                      height="16"
                      class="color-icon ms-2"
                      viewBox="0 0 24 24"
                      role="img"
                      aria-hidden="true"
                    >
                      <path
                        d="M13.9467 12L9.8735 7.92701C9.73517 7.78851 9.66433 7.61443 9.661 7.40476C9.65783 7.19526 9.72867 7.01801 9.8735 6.87301C10.0185 6.72818 10.1942 6.65576 10.4005 6.65576C10.6068 6.65576 10.7825 6.72818 10.9275 6.87301L15.4217 11.3673C15.5152 11.4609 15.5813 11.5597 15.6198 11.6635C15.6583 11.7673 15.6775 11.8795 15.6775 12C15.6775 12.1205 15.6583 12.2327 15.6198 12.3365C15.5813 12.4403 15.5152 12.5391 15.4217 12.6328L10.9275 17.127C10.789 17.2653 10.6149 17.3362 10.4052 17.3395C10.1957 17.3427 10.0185 17.2718 9.8735 17.127C9.72867 16.982 9.65625 16.8063 9.65625 16.6C9.65625 16.3937 9.72867 16.218 9.8735 16.073L13.9467 12Z"
                      ></path>
                    </svg>
                  </a>
                </li>
              </ul>
            </div>
          </nav>
        </div>
      </div>

      <!-- 右側ドロップダウン -->
      <div class="col-8 d-flex align-items-center justify-content-center">
        col-8
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "Sample",
  data() {
    return {
      navItems: ["Home", "Features", "Pricing", "Disabled"],
    };
  },
};
</script>

<style scoped>
.color-icon {
  fill: currentColor;
}
</style>
