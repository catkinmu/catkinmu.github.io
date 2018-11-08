
<template>
  <Layout class="layout">
    <Header class="layout-hidder">Header</Header>
    <Layout>
      <Sider hide-trigger>Sider</Sider>
      <Content class="layout-content">Content</Content>
    </Layout>
  </Layout>
</template>
<script>
export default {

}
</script>
<style scoped>
.layout {
  height: 100%;
  /* border: 1px solid #d7dde4;
  background: #f5f7f9;
  position: relative;
  border-radius: 4px;
  overflow: hidden; */
}
.layout-hidder,
.layout-sider {
  width: 100%;
}
.layout-content {
  margin: 10px;
  padding: 10px;
  background: #ffffff;
  /* background-clip: content-box; */
}
.layout-logo {
  width: 100px;
  height: 30px;
  background: #5b6270;
  border-radius: 3px;
  float: left;
  position: relative;
  top: 15px;
  left: 20px;
}
.layout-nav {
  width: 420px;
  margin: 0 auto;
  margin-right: 20px;
}
</style>