<template lang="html">
  <div class="about">
    <nav-header></nav-header>
    <div class="headpic">
      <div class="container headtitle full">
        <div class="title">
          <h1 href="/blog">freedom</h1>
        </div>
      </div>
    </div>
    <div class="container full">
      <div class="list">
        <div>
          <div class="full-content">
            <div class="messages-text post-content">
              <div style="height: 600px;">
                <h2 style="margin-bottom: 20px;">About</h2>
                <strong>个人博客-记录我的点点滴滴</strong>
                <br>
                <p style="margin-bottom: 20px;padding-top: 20px;">
                  csdn博客: <a href="https://blog.csdn.net/wwq147852">https://blog.csdn.net/wwq147852</a>
                </p>
                以后，再也不用去csdn博客发表审核博客了。
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <nav-footer></nav-footer>
  </div>
</template>

<script>
import NavHeader from '@/components/Header.vue'
import NavFooter from '@/components/Footer.vue'
export default {
  components: {
    NavHeader,
    NavFooter,
  }
}
</script>

<style lang="css">
.about {
  background-color: #fff;
}
@media (max-width: 800px) {
  .about img {
    width: 100%;
  }
}
</style>
