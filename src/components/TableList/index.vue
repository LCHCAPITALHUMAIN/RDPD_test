<template lang="pug">
  <div>
      <md-table v-model="users" md-card>
        <md-table-toolbar>
          <h1 class="md-title">Users</h1>
        </md-table-toolbar>

        <md-table-row slot="md-table-row" slot-scope="{ users }">
          <md-table-cell md-label="ID" md-sort-by="id" md-numeric>{{ users.id }}</md-table-cell>
          <md-table-cell md-label="Name" md-sort-by="name">{{ users.url }}</md-table-cell>
          <md-table-cell md-label="Email" md-sort-by="email">{{ users.domain }}</md-table-cell>
        </md-table-row>
      </md-table>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Users",
  data() {
    return {
      users: null,
    };
  },
  created: function () {
    axios
      .get(
        "https://cdn.inpixio.com/www-docs/prod/inpixio.com/audit_rgpd/lp.json"
      )
      .then((res) => {
        console.log(res);
        this.users = res.data;
      });
  },
};
/*import axios from "axios";
import axios from "axios";

export default {
  name: "Users",
  data() {
    return {
      users: null
    };
  },
  created: function() {
    axios.get("https://cdn.inpixio.com/www-docs/prod/inpixio.com/audit_rgpd/lp.json").then(res => {
      console.log(res)
      this.users = res.data;
    });
  }
};
*/
</script>
<style lang="sass">
</style>
