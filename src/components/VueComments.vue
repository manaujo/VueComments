<template>
  <div class="container">
    <h1>Comentarios</h1>
    <form class="mb-3">
      <div class="mb-3">
        <label for="name" class="form-label">Nome</label>
        <input type="text" class="form-control" id="name" v-model="name" />
      </div>
      <div class="mb-3">
        <label for="comments" class="form-label">Comentario</label>
        <textarea
          type="text"
          class="form-control"
          id="comments"
          style="height: 100px"
          v-model="message"
        ></textarea>
      </div>
      <button
        type="submit"
        class="btn btn-primary"
        v-on:click.prevent="addComments"
      >
        Confirmar
      </button>
    </form>

    <div class="list-group mb-3">
      <div
        class="list-group-item"
        v-for="(comment, index) in comments"
        :key="index"
      >
        <span class="comment__author"
          >Autor: <strong>{{ comment.name }}</strong></span
        >
        <p>{{ comment.message }}</p>
        <div>
          <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)">Excluir</a
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "VueComments",
  data() {
    return {
      comments: [],
      name: "",
      message: "",
    };
  },
  methods: {
    addComments() {
      if (this.name.trim() === "" || this.message.trim() === "") {
        return;
      }
      this.comments.push({
        name: this.name,
        message: this.message,
      });
      this.name = "";
      this.message = "";
    },
    removeComment(index) {
      this.comments.splice(index, 1);
    },
  },
};
</script>
