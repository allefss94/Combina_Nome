<template>
  <div>
    <div id="slogan" class="text-center">
      <h1>Combina Nome</h1>
      <br />
      <h6 class="text-secondary">
        Gerador de nomes utilizando Vue.js, GraphQL e Node
      </h6>
    </div>
    <div id="main">
      <domainsList></domainsList>
    </div>
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css";
import "font-awesome/css/font-awesome.css";
import domainsList from "./components/domainsList";

export default {
  name: "App",
  components: {
    domainsList,
  },
};
</script>

<style>
#slogan {
  margin-top: 30px;
  margin-bottom: 30px;
}

#main {
  background-color: #f1f1f1;
  padding-top: 20px;
  padding-bottom: 20px;
}

a {
  text-decoration: none;
}
a span {
  color: #fff;
}
</style>
