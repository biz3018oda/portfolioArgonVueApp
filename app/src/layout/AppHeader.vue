<template>
  <header class="header-global">
    <base-nav type="secondary" effect="light" expand>
      <a class="navbar-brand" href="#">PORTFOLIO</a>

      <div class="row" slot="content-header" slot-scope="{ closeMenu }">
        <div class="col-6 collapse-brand">
          <a
            href="https://demos.creative-tim.com/vue-argon-design-system/documentation/"
          >
            <img
              src="https://demos.creative-tim.com/vue-argon-design-system/img/brand/blue.png"
            />
          </a>
        </div>
        <div class="col-6 collapse-close">
          <close-button @click="closeMenu"></close-button>
        </div>
      </div>

      <ul class="navbar-nav ml-lg-auto">
        <li class="nav-item">
          <a class="nav-link nav-link-icon nav-link-inter nav-color" href="#">
            おすすめ
          </a>
        </li>
        <li class="nav-item">
          <a class="nav-link nav-link-icon nav-link-inter nav-color" href="#">
            新着
          </a>
        </li>
      </ul>

      <div class="ml-lg-auto">
        <base-button type="secondary">ログイン</base-button>
        <base-button type="default">会員登録</base-button>
      </div>
    </base-nav>
  </header>
</template>
<script>
import BaseNav from "@/components/BaseNav";
import BaseDropdown from "@/components/BaseDropdown";
import CloseButton from "@/components/CloseButton";

export default {
  components: {
    BaseNav,
    CloseButton,
    BaseDropdown,
  },
};
</script>
<style>
.navbar-collapse .navbar-brand {
  font-size: 20px;
  font-family: "Inter", sans-serif;
  font-weight: 700;
}
.navbar-nav .nav-item .nav-link-inter {
  font-family: "Inter", sans-serif;
  font-weight: 700;
}

.navbar-light .navbar-nav .nav-link.nav-link-inter {
  color: #000000;
}
</style>
