<template>
  <div class="col-sm-4">
    <h1 style="text-align: left">Member's names</h1>
    <ag-grid-vue
      style="width: 620px; height: 620px;"
      class="ag-theme-balham"
      :columnDefs="newColumns"
      :rowData="characters"
      :animateRows="true"
      :pagination="true"
      paginationPageSize="20"
    >
    </ag-grid-vue>
  </div>
</template>

<script>
import { AgGridVue } from "ag-grid-vue";

export default {
  name: "Characters",
  components: {
    AgGridVue,
  },

  data() {
    return {
      newColumns: [],
      characters: [],
    };
  },

  methods: {
    lastNames: function(characters) {
      var names = [];

      characters.forEach(function(character) {
        character.lastName = character.name
          .split(" ")
          .slice(-1)
          .join(" ");
        character.characterName = character.name
          .split(" ")
          .slice(0, 1)
          .join(" ");
        names.push(character);
      });

      return names;
    },
  },

  mounted() {
    this.newColumns = [
      {
        headerName: "Name",
        field: "characterName",
        sortable: true,
        filter: true,
        pagination: true,
      },
      {
        headerName: "Last name",
        field: "lastName",
        sortable: true,
        filter: true,
        pagination: true,
      },
      {
        headerName: "Blood Status",
        field: "bloodStatus",
        sortable: true,
        filter: true,
        pagination: true,
      },
    ];

    fetch(
      "https://www.potterapi.com/v1/characters?key=$2a$10$NZHpGsHFHKI3fzDGqfgcLuxyX7OnPFi43Bljly7IgslS84AA9j82G"
    )
      .then((result) => result.json())
      .then((characters) => (this.characters = this.lastNames(characters)));
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
@import "../../node_modules/ag-grid-community/dist/styles/ag-grid.css";
@import "../../node_modules/ag-grid-community/dist/styles/ag-theme-balham.css";
.col-sm-4 {
  margin-left: 10%;
}
</style>
