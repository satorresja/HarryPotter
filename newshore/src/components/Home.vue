<template>
  <div class="col-sm-3">
    <h1 style="text-align: left">Houses</h1>
    <ag-grid-vue
      style="width: 405px; height: 150px;"
      class="ag-theme-balham"
      :columnDefs="columnDefs"
      :rowData="houses"
      :animateRows="true"
    >
    </ag-grid-vue>
  </div>
</template>

<script>
import { AgGridVue } from "ag-grid-vue";

export default {
  name: "Houses",
  components: {
    AgGridVue,
  },
  data() {
    return {
      columnDefs: [],
      houses: [],
    };
  },
  created() {
    this.columnDefs = [
      { headerName: "House", field: "name", sortable: true, filter: true },
      {
        headerName: "Number of members",
        field: "members.length",
        sortable: true,
      },
    ];

    fetch(
      "https://www.potterapi.com/v1/houses?key=$2a$10$NZHpGsHFHKI3fzDGqfgcLuxyX7OnPFi43Bljly7IgslS84AA9j82G"
    )
      .then((result) => result.json())
      .then((houses) => (this.houses = houses));
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
@import "../../node_modules/ag-grid-community/dist/styles/ag-grid.css";
@import "../../node_modules/ag-grid-community/dist/styles/ag-theme-balham.css";
.col-sm-3 {
  margin-left: 10%;
}
</style>
