<template>
  <div>
    <h5>
      {{title}}
      <span class="badge badge-info">{{ items.length }}</span>
    </h5>
    <div class="card">
      <div class="card-body">
        <ul class="list-group">
          <li class="list-group-item" v-for="item in items" v-bind:key="item.id">
            <div class="row">
              <div class="col-md">{{ item.description }}</div>
              <div class="col-md text-right">
                <button v-on:click="deleteItem(item)" class="btn btn-danger btn-sm">
                  <span class="fa fa-trash" />
                </button>
              </div>
            </div>
          </li>
        </ul>
        <br />
        <div class="input-group">
          <input
            v-model="description"
            v-on:keyup.enter="addItem(type, description)"
            class="form-control"
            type="text"
            placeholder="Digite o item"
          />
          <div class="input-group-append">
            <button v-on:click="addItem(type, description)" class="btn btn-info">
              <span class="fa fa-plus"></span>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AppItemList",
  props: ["title", "type", "items"],
  data() {
    return {
      description: ""
    };
  },
  methods: {
    addItem(type, description) {
      this.$emit("addItem", { type, description });
      this.description = "";
    },
    deleteItem(item) {
      this.$emit("deleteItem", item);
    }
  }
};
</script>
 
<style scoped>
</style>
