<template>
  <div>
    <div id="main">
      <div class="container">
        <div class="row">
          <div class="col-md">
            <h5>
              Nome
              <span class="badge badge-info">{{ prefixes.length }}</span>
            </h5>
            <itemList
              v-bind:items="prefixes"
              @addItem="addPrefix"
              @deleteItem="deletePrefix"
            ></itemList>
          </div>

          <div class="col-md">
            <h5>
              Sobrenomes
              <span class="badge badge-info">{{ sufixes.length }}</span>
            </h5>
            <itemList
              v-bind:items="sufixes"
              @addItem="addSufix"
              @deleteItem="deleteSufix"
            ></itemList>
          </div>
        </div>
        <div class="row mt-4">
          <div class="col-md">
            <h5>
              Combinações posssíveis
              <span class="badge badge-info">{{ domains.length }}</span>
            </h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li
                    class="list-group-item"
                    v-for="domain in domains"
                    :key="domain.name"
                  >
                    <div class="row">
                      <div class="col-md">
                        {{ domain.name }}
                      </div>
                      <div class="col-md text-right">
                        <a
                          class="btn btn-info"
                          v-bind:href="domain.checkout"
                          target="_blank"
                        >
                          <span class="fa fa-search"></span>
                        </a>
                      </div>
                    </div>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css";
import "font-awesome/css/font-awesome.css";
import itemList from "./itemList";

export default {
  name: "App",
  components: {
    itemList,
  },
  data() {
    return {
      prefix: "",
      sufix: "",
      prefixes: ["Air", "Jet", "Flight"],
      sufixes: ["Hub", "Station", "Mart"],
    };
  },
  methods: {
    addPrefix(prefix) {
      this.prefixes.push(prefix);
      this.prefix = "";
    },

    deletePrefix(prefix) {
      this.prefixes.splice(this.prefixes.indexOf(prefix), 1);
    },

    addSufix(sufix) {
      this.sufixes.push(sufix);
      this.sufix = "";
    },

    deleteSufix(sufix) {
      this.sufixes.splice(this.sufixes.indexOf(sufix), 1);
    },
  },
  computed: {
    domains() {
      const domains = [];
      for (const prefix of this.prefixes) {
        for (const sufix of this.sufixes) {
          let name = `${prefix} ${sufix}`;
          const checkout = `https://www.dicionariodenomesproprios.com.br/busca.php?q=${prefix}-${sufix}`;
          domains.push({
            name,
            checkout,
          });
        }
      }
      return domains;
    },
  },
};
</script>

<style></style>
