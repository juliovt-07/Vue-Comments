<template>
  <div class="container">
    <h1>Comentários</h1>
    <hr />
    <FormTodo v-on:add-comment="addComment"></FormTodo>
    <div class="list-group">
      <div
        class="list-group-item"
        v-for="(comment, index) in allComments"
        :key="(comment.name, comment.message)"
      >
        <span>
          Author:
          <strong>{{ comment.name }}</strong>
        </span>
        <p>{{ comment.message }}</p>
        <div>
          <a id="deleteButton" v-on:click.prevent="removeComment(index)">Excluir</a>
        </div>
      </div>
    </div>
    <hr />
  </div>
</template>

<script>
import FormTodo from "./FormTodo";

export default {
  components: {
    FormTodo
  },
  data() {
    return {
      comments: []
    };
  },
  methods: {
    removeComment(index) {
      this.comments.splice(index, 1);
    },
    addComment(comment){
        this.comments.push(comment)
    }
  },
  computed: {
    allComments() {
      return this.comments.map(comment => ({
        //Ainda falta eu saber mais sobre 'MAP'
        ...comment,
        name: comment.name.trim() === "" ? "Anônimo" : comment.name
      }));
    }
  },
  watch: {
    comments(val) {
      console.log("val", val);
    }
  }
};
</script>