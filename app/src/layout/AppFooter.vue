<template>
  <footer class="bg-dark text-white pt-5 pb-4">
    <div class="container text-md-left">
      <div class="row">
        <!-- ロゴ＆説明 -->
        <div class="col-md-3 col-lg-3 col-xl-3 mx-auto mb-4">
          <h6 class="text-uppercase fw-bold mb-4 text-white">MyCompany Inc.</h6>
          <p class="mb-1">〒123-4567</p>
          <p class="mb-1">東京都新宿区西新宿1-2-3</p>
          <p class="mb-0">TEL: 03-1234-5678</p>
          <p class="mb-0">Email: info@mycompany.com</p>
        </div>

        <!-- サイトリンク -->
        <div class="col-md-2 col-lg-2 col-xl-2 mx-auto mb-4">
          <h6 class="text-uppercase fw-bold mb-4 text-white">サイトリンク</h6>
          <p><a href="#" class="text-white text-decoration-none">ホーム</a></p>
          <p>
            <a href="#" class="text-white text-decoration-none">サービス</a>
          </p>
          <p>
            <a href="#" class="text-white text-decoration-none">会社情報</a>
          </p>
          <p>
            <a href="#" class="text-white text-decoration-none">お問い合わせ</a>
          </p>
        </div>

        <!-- サポートリンク -->
        <div class="col-md-3 col-lg-2 col-xl-2 mx-auto mb-4">
          <h6 class="text-uppercase fw-bold mb-4 text-white">サポート</h6>
          <p><a href="#" class="text-white text-decoration-none">FAQ</a></p>
          <p>
            <a href="#" class="text-white text-decoration-none"
              >ヘルプセンター</a
            >
          </p>
          <p>
            <a href="#" class="text-white text-decoration-none"
              >プライバシーポリシー</a
            >
          </p>
          <p>
            <a href="#" class="text-white text-decoration-none">利用規約</a>
          </p>
        </div>

        <!-- ソーシャルリンク -->
        <div class="col-md-4 col-lg-3 col-xl-3 mx-auto mb-md-0 mb-4">
          <h6 class="text-uppercase fw-bold mb-4 text-white">ソーシャル</h6>
          <a href="#" class="text-white me-4"><i class="bi bi-facebook"></i></a>
          <a href="#" class="text-white me-4"><i class="bi bi-twitter"></i></a>
          <a href="#" class="text-white me-4"
            ><i class="bi bi-instagram"></i
          ></a>
          <a href="#" class="text-white me-4"><i class="bi bi-linkedin"></i></a>
        </div>
      </div>
    </div>

    <!-- コピーライト -->
    <div class="text-center p-3 mt-3 border-top border-secondary">
      © 2025 MyCompany. All rights reserved.
    </div>
  </footer>
</template>
<script>
export default {
  name: "app-footer",
  data() {
    return {
      year: new Date().getFullYear(),
    };
  },
};
</script>
<style></style>
