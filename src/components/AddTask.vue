<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Name</label>
      <input type="text" v-model="name" name="text" placeholder="Add name" />
    </div>
    <div class="form-control">
      <label>Relative Relation</label>
      <input
        type="text"
        v-model="relation"
        name="day"
        placeholder="Add Relative Relation "
      />
    </div>
    <div class="form-control form-control-check">
      <label>Set Importance</label>
      <input type="checkbox" v-model="important" name="reminder" />
    </div>

    <input type="submit" value="Save Person" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: 'AddTask',
  data() {
    return {
      name: '',
      relation: '',
      important: false,
    }
  },
  methods: {
    onSubmit(e) {
      e.preventDefault()

      if (!this.name) {
        alert('Please add a name')
        return
      }

      const newTask = {
        // id: Math.floor(Math.random() * 100000),
        name: this.name,
        relation: this.relation,
        important: this.important,
      }

      this.$emit('add-task', newTask)

      this.name = ''
      this.relation = ''
      this.important = false
    },
  },
}
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}

.form-control {
  margin: 20px 0;
}

.form-control label {
  display: block;
}

.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}

.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.form-control-check label {
  flex: 1;
}

.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>
