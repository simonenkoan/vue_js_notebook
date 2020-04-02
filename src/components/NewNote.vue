<template>
  
  <div class="new-note">
    <!-- <div>
      Click the values to edit!
      <ul class="todo-list">
        <li v-for="todo in todos">
          <input
            v-if="todo.edit"
            v-model="todo.title"
            @blur="todo.edit = false; $emit('update')"
            @keyup.enter="todo.edit=false; $emit('update')"
            v-focus
          />
          <div v-else>
            <label @click="todo.edit = true;">{{todo.title}}</label>
          </div>
        </li>
      </ul>
    </div> -->
    <div class="meggage-error" v-if="message_blank">
      <!-- <p>{{message_blank}}</p> -->
    </div>
    <div style="text-align: center;" class="note-title">
      <label for>Title</label>
      <input type="text" v-model="note.title" />
    </div>
    <div class="note-title">
      <p>Please select priority:</p>
      <div class="note-radio-left">
        <input
          style="cursor: pointer; margin-right: 5px"
          class="note-radio"
          type="radio"
          id="low"
          name="priority"
          value="low"
          v-model="note.priority"
          checked="checked"
        />
        <label style="cursor: pointer; margin-right: 5px" class="note-radio" for="low">low</label>
        <br />
        <input
          style="cursor: pointer; margin-right: 5px"
          class="note-radio"
          type="radio"
          id="standart"
          name="priority"
          value="standart"
          v-model="note.priority"
        />
        <label style="cursor: pointer; margin-right: 5px" class="note-radio" for="standart">standart</label>
        <br />
        <input
          style="cursor: pointer; margin-right: 5px"
          class="note-radio"
          type="radio"
          id="high"
          name="priority"
          value="high"
          v-model="note.priority"
        />
        <label style="cursor: pointer; margin-right: 5px" class="note-radio" for="high">high</label>
        <br />
      </div>
    </div>
    <div class="note-descr">
      <label for>Description</label>
      <textarea v-model="note.description"></textarea>
      <button class="btn btnPrimary" @click="addNote">New Note</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todos: [
        { title: "one value", edit: false },
        { title: "one value", edit: false },
        { title: "otro titulo", edit: false }
      ],
      editedTodo: null,
      message: "Hello Vue.js!"
    };
  },
  props: {
    note: {
      type: Object,
      required: true
    }
  },
  methods: {
    addNote() {
      this.$emit("addNote", this.note);
    },
    editTodo: function (todo) {
      this.editedTodo = todo
    }
  },
  directives: {
    focus: {
      inserted (el) {
        el.focus()
      }
    }
  }
};
</script>

<style lang="scss">
.new-note {
  text-align: center;
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  flex-wrap: wrap;
  label,
  input,
  button {
    margin: 10px 0;
    display: inline;
  }
  .note-radio {
    width: 10%;
  }
  .note-title {
    width: 48%;
    // padding: 18px 20px;
    // margin-bottom: 20px;
  }
  .note-descr {
    text-align: center;
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    width: 100%;
    padding: 18px 20px;
    margin-bottom: 20px;
    justify-content: center;
  }
  .note-radio-left {
    // text-align: center;
    // width: 40%;
    // align-items: center;
    width: 150px;
    margin: auto;
    padding-left: 30px;
    text-align: justify;
  }
}
</style>