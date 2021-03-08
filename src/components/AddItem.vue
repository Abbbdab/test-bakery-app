<template>
  <div class="container">
    <div class="table-container">
      <br />
      <table>
        <colgroup>
          <col style="width: 10%" />
          <col style="width: 20%" />
          <col style="width: 50%" />
        </colgroup>
        <thead class="bold">
          <tr>
            <th>No.</th>
            <th><a @click="sort('name')" href="#">Name</a></th>
            <th><a @click="sort('topping')" href="#">Topping / Frosting</a></th>
            <th><a @click="sort('type')" href="#">Type</a></th>
          </tr>
        </thead>

        <tbody class="regular">
          <tr v-for="(item, index) in items" :key="index">
            <td>{{ index + 1 }}</td>
            <td>{{ item.name }}</td>
            <td>{{ item.topping }}</td>
            <td>{{ item.type }}</td>
          </tr>
        </tbody>
      </table>
    </div>
    <br />

    <div class="item-form">
      <button class="add-btn bold" v-on:click="form = !form">Add Item</button>
      <form @submit.prevent="addItem" class="form" v-if="form">
        <div class="form-group">
          <button class="cls-btn" v-on:click="form = !form">&#10006;</button>
          <label for="item-name" class="bold">Name</label>
          <input
            class="regular"
            type="text"
            name="item-name"
            v-model.lazy.trim="newItem.name"
            required
          /><br />
          <label for="topping-name" class="bold">Topping</label>
          <input
            class="regular"
            type="text"
            name="topping-name"
            v-model.lazy.trim="newItem.topping"
          /><br />
          <label for="type-name" class="bold">Type</label>
          <input
            class="regular"
            type="text"
            name="type-name"
            v-model.lazy.trim="newItem.type"
          /><br />
        </div>
        <br />
        <button class="submit-btn bold" type="submit">Add to Inventory</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "newItem",
  data() {
    return {
      origItems: [
        {
          name: "Classic",
          topping: "Glazed",
          type: "donut",
        },
        {
          name: "Oreo",
          topping: "Oreo and Cream",
          type: "donut",
        },
        {
          name: "Nutella",
          topping: "Nutella Filling",
          type: "donut",
        },
        {
          name: "Apple Pie",
          topping: "Apple Filling",
          type: "pie",
        },
        {
          name: "Pecan Pie",
          topping: "Pecan Filling with Cream",
          type: "pie",
        },
        {
          name: "Carrot Cake",
          topping: "Carrots and Cream",
          type: "cake",
        },
        {
          name: "Black Forrest Cake",
          topping: "Dark Chocolate, White Chocolate and Mint",
          type: "cake",
        },
      ],
      form: false,
      newItem: {},
      sortType: "",
    };
  },

  computed: {
    //Function to sort items
    items() {
      if (this.sortType === "") return this.origItems;

      //Sort items by Name
      if (this.sortType === "name") {
        return this.origItems.slice().sort((a, b) => {
          if (a.name < b.name) return -1;
          if (a.name > b.name) return 1;
          return 0;
        });
      }

      //Sort items by Topping
      if (this.sortType === "topping") {
        return this.origItems.slice().sort((a, b) => {
          if (a.topping < b.topping) return -1;
          if (a.topping > b.topping) return 1;
          return 0;
        });
      }

      //Sort items by Type
      if (this.sortType === "type") {
        return this.origItems.slice().sort((a, b) => {
          if (a.type < b.type) return -1;
          if (a.type > b.type) return 1;
          return 0;
        });
      } else {
        return this.origItems;
      }
    },
  },

  methods: {
    sort(type) {
      this.sortType = type;
    },

    //Function to add items
    addItem() {
      this.origItems.push(this.newItem);
      this.newItem = {};
    },
  },
};
</script>

<style lang="scss" scoped>
.table-container {
  display: grid;
  place-items: center;
}

table {
  width: 90%;
  table-layout: fixed;
  border-radius: 5px;
  font-size: 20px;
  border-collapse: collapse;
  text-align: left;

  td,
  th {
    padding: 10px;
    border-bottom: 1px solid;
  }

  thead {
    font-size: 24px;
    color: #bf3636;
    border-bottom: 2px solid #bf3636;
  }

  a {
    text-decoration: none;
    color: #bf3636;
    :visited {
      color: #bf3636;
      text-decoration: none;
    }
  }

  a:hover {
    text-decoration: underline;
  }
}

.item-form {
  width: 90%;
  margin-top: 30px;
  display: grid;
  place-content: center;
  background: #f2f2f0;

  .add-btn {
    font-size: 18px;
    padding: 10px 12px;
    border-radius: 8px;
    width: 180px;
    border: none;
    background-color: #bf3636;
    color: #f2f2f0;
    float: left;
    margin-bottom: 25px;
    z-index: 3;
  }

  .form {
    background-color: #f2f2f0;
    display: grid;
    place-items: center;
    width: 120%;
    text-align: left;
    border-radius: 8px;
    box-shadow: 4px 10px 55px -7px rgba(173, 173, 172, 1);
    -webkit-box-shadow: 4px 10px 55px -7px rgba(173, 173, 172, 1);
    -moz-box-shadow: 4px 10px 55px -7px rgba(173, 173, 172, 1);

    .cls-btn {
      width: 40px;
      height: auto;
      background-color: transparent;
      border: none;
      font-size: 24px;
      color: #bf3636;
      margin-left: 90%;
      margin-bottom: 30px;
    }

    .form-group {
      display: grid;
      label {
        font-size: 18px;
        width: fit-content;
        z-index: 1;
        margin-left: 10px;
        background-color: #f2f2f0;
      }

      input {
        width: 400px;
        margin: -10px 0px 12px 0px;
        padding: 10px;
        font-size: 14px;
        background-color: transparent;
        border: 1px solid #bf3636;
        border-radius: 4px;
      }
    }

    .submit-btn {
      font-size: 18px;
      padding: 10px 12px;
      border-radius: 8px;
      width: 180px;
      border: none;
      background-color: #bf3636;
      color: #f2f2f0;
      margin-top: -18px;
      margin-left: 80px;
    }
  }
}
</style>