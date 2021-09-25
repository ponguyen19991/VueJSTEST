<template>
  <div id="app">
    <SinglePage />
    <Home />
  </div>
</template>

<script>
import SinglePage from "./components/SinglePage";
import Home from "./views/Home";
export default {
  name: "App",
  components: {
    SinglePage,
    Home,
  },
}
</script>

<style>

</style>