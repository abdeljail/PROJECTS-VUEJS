<template>
  <div>
    <div class="todolist">
      <div class="header-todolist">
        <input
          v-model="contentTack"
          type="search"
          name="enter"
          id="enter"
          placeholder="endter tack"
        />
        <button @click="addTack">add tack</button>
      </div>
      <div class="body-todolist">
        <div class="empty-tack" v-if="arrayTack.length === 0">
          this todo is empty
        </div>
        <div
          v-else
          class="box-tack"
          v-for="(tack, index) in getTack"
          :key="index"
        >
          <div>{{ tack }}</div>
          <div>
            <button @click="editTack(index)">edit</button>
          </div>
          <div>
            <button @click="deleteTack(index)">delete</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "todoList",
  data() {
    return {
      contentTack: "",
      arrayTack: [],
      varaibleEditTack: null,
    };
  },
  methods: {
    addTack() {
      if (!this.contentTack) return;
      if (this.arrayTack.includes(this.contentTack)) return;
      if (typeof this.varaibleEditTack === "number") {
        this.arrayTack[this.varaibleEditTack] = this.contentTack;
        this.contentTack = "";
        this.varaibleEditTack = null;
        return;
      }
      this.arrayTack.push(this.contentTack);
      this.contentTack = "";
    },
    deleteTack(index) {
      this.arrayTack.splice(index, 1);
    },
    editTack(index) {
      this.contentTack = this.arrayTack[index];
      this.varaibleEditTack = index;
      console.log(this.varaibleEditTack);
    },
  },
  computed: {
    getTack() {
      return this.arrayTack;
    },
  },
};
</script>

<style>
.todolist {
  padding: 20px 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 500px;
  background: #151e31;
}
.todolist > div {
  padding: 20px 0;
  width: 400px;
  display: flex;
}

.header-todolist {
  display: flex;
  align-items: center;
}
.header-todolist input {
  flex-grow: 3;
  outline: none;
  border: none;
  padding: 20px 15px;
  border-radius: 4px 0px 0px 4px;
}
.header-todolist button {
  flex-grow: 1;
  cursor: pointer;
  outline: none;
  border: none;
  padding: 20px 15px;
  text-transform: capitalize;
  color: #fff;
  background-color: #07884b;
}
.todolist .body-todolist {
  flex-direction: column;
}
.todolist .body-todolist .empty-tack {
  background-color: #fff;
  padding: 20px 10px;
  text-align: center;
  text-transform: capitalize;
  border: 3px dashed #151e31;
}
.todolist .body-todolist .box-tack {
  padding: 20px 10px;
  background-color: #eee;
  margin: 3px 0;
  border-radius: 4px;
  display: flex;
}
.todolist .body-todolist .box-tack div:first-child {
  flex-grow: 3;
  display: flex;
  align-items: center;
}
.todolist .body-todolist .box-tack div:not(div:first-child) {
  flex-grow: 0;
  padding: 0 4px;
}
.todolist .body-todolist div:not(div:first-child) button {
  padding: 6px 10px;
  border: none;
  outline: none;
  cursor: pointer;
  border-radius: 4px;
  color: #fff;
  transition: 0.3s ease;
  text-transform: capitalize;
}
.todolist .body-todolist .box-tack div:nth-child(2) button {
  background-color: #64acecab;
}
.todolist .body-todolist .box-tack div:nth-child(2) button:hover {
  background-color: #64acec;
}
.todolist .body-todolist .box-tack div:last-child button {
  background-color: #e86767a3;
}
.todolist .body-todolist .box-tack div:last-child button:hover {
  background-color: #e86767;
}
</style>
