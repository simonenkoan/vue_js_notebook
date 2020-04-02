<template>
  <div class="notes">
    <div
      class="note"
      :class="[ {full: !grid}, {
            lowpriority: note.priority === lowpriority,
            highpriority: note.priority === highpriority,
            standartpriority: note.priority === standartpriority,} ]"
      v-for="(note, index) in notes"
      :key="index"
    >
      <div class="note-header">
        <p>{{note.title }}</p>
        <p style="cursor: pointer" @click="removeNote(index)">x</p>
        <!-- <SomeIcon style="cursor: pointer" /> -->
      </div>
      <div class="note-body">
        <p>{{note.description}}</p>
        <span>{{note.date}}</span>
        <br />
        <span>{{note.priority}}</span>
      </div>
    </div>
  </div>
</template>

<script>
// import SomeIcon from "../assets/basic_trashcan_remove.svg";
export default {
  //   components: {
  //     SomeIcon
  //   },
  data() {
    return {
      lowpriority: "low",
      highpriority: "high",
      standartpriority: "standart"
    };
  },
  props: {
    notes: {
      type: Array,
      required: true
    },
    grid: {
      type: Boolean,
      required: true
    }
  },
  //   data() {
  //     return {
  //       priorityclass: this.notes,
  //       active: true,
  //       "text-danger": true
  //     };
  computed: {
    classObject() {
      return {
        notepriority: this.note.priority === "low"
      };
    }
  },
  methods: {
    removeNote(index) {
      console.log(`Note removed ${index}`);
      this.$emit("remove", index);
    }
  }
};
</script>

<style lang="scss">
.notes {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  padding: 40px 0;
}
.note {
  width: 48%;
  padding: 18px 20px;
  margin-bottom: 20px;
  background-color: #ffffff;
  box-shadow: 0 5px 5px rgb(214, 217, 224);
  transition: all 0.25s cubic-bezier(0.02, 0.01, 0.47, 1);
  &.full {
    width: 100%;
    text-align: center;
  }
  &.lowpriority {
    background-color: rgba(132, 252, 132, 0.301);
  }
  &.highpriority {
    background-color: rgba(227, 105, 252, 0.144);
  }
  &.standartpriority {
    background-color: rgba(210, 255, 174, 0.144);
  }
  &:hover {
    box-shadow: 0 20px 20px rgb(214, 217, 224);
    transform: translate(0, -6px);
  }
}
.note-body {
  p {
    color: #999999;
  }
  span {
    font-size: 14px;
    color: #999;
  }
}
.note-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  h1 {
    font-size: 32px;
  }
  p {
    color: #999999;
    font-size: 22px;
  }
  svg {
    margin-right: 12px;
    color: #999999;
    &.active {
      color: #348cff;
    }
    &:last-child {
      margin-right: 0;
    }
  }
  &.full {
    justify-content: center;
    p {
      margin-right: 20px;
      &:last-child {
        margin-right: 0px;
      }
    }
  }
}
</style>
