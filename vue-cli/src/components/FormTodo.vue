<template>
  <div class="form-group">
    <p>
      <input type="text" class="form-control" placeholder="Seu Nome" v-model="name" />
    </p>
    <p>
      <textarea class="form-control" placeholder="Comentário" v-model="comment"></textarea>
    </p>
    <a href="#" class="btn btn-primary" v-on:click="addComment" type="submit">Comentar</a>
  </div>
</template>

<script>
export default {
    data() {
        return {
            name: '',
            comment: ''
            
        }
    },
    methods: {
        addComment() {
        if (this.comment.trim() === "") {
            return;
        }
        this.$emit('add-comment', {
            name: this.name,
            comment: this.comment
        });

        (this.name = ""), (this.comment = "");
        }
    }
}
</script>