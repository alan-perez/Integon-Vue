<template>
  <div class="container">
    <h2>Shopping list</h2>
    <div class="user-input">
      <input v-model="input" placeholder="Press enter to add new item" /><button
        @click="addItem"
        >Add item</button
      >
    </div>

    <div>
      <ul>
        <li v-for="item in items" :key="item"
          >{{ item }}
          <button class="button--remove" @click="deleteItem(item)"
            >Delete</button
          ></li
        >
      </ul>
    </div>
    <button class="button--delete" @click="deleteAll">Delete All</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      input: '',
      items: [],
    }
  },
  methods: {
    addItem() {
      if (!this.input) {
        return
      }
      this.items.push(this.input)
      this.input = ''
    },
    deleteItem(value) {
      this.items = this.items.filter(item => item !== value)
    },
    deleteAll() {
      this.items.splice(this.items)
    },
  },
}
</script>

<style lang="scss">
@import 'styles/global';

$color-green: #4fc08d;
$color-grey: #2c3e50;

.container {
  max-width: 600px;
  margin: 80px auto;
}

.item {
  display: flex;
  justify-content: space-between;
}

// Type
.h2 {
  font-size: 21px;
}

.user-input {
  display: flex;
  align-items: center;
  padding-bottom: 20px;
  input {
    width: 100%;
    padding: 10px 6px;
    margin-right: 10px;
  }
}

.item {
  display: flex;
  align-items: center;
}

// Buttons
button {
  appearance: none;
  padding: 10px;

  font-weight: bold;
  border-radius: 10px;
  border: none;
  background: $color-grey;
  color: white;
  white-space: nowrap;

  + button {
    margin-left: 10px;
  }
}

.button--delete {
  display: block;
  margin: 0 auto;
  background: red;
}

.button--remove {
  background: none;
  color: red;
  text-transform: uppercase;
  font-size: 11px;
  align-self: flex-end;
}

ul {
  display: block;
  margin: 0 auto;
  padding: 30px;
  border: 1px solid rgba(0, 0, 0, 0.25);

  > li {
    color: $color-grey;
    margin-bottom: 4px;
  }
}
</style>
