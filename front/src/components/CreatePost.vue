<template>
  <div>
    <v-layout row class="create">
      <v-flex xs12 class="text-xs-center mt-2">
        <!-- <h2 style="font-size: 250px;" class="title">Here you can create a new post</h2> -->
      </v-flex>
    </v-layout>
    <v-layout row align-center justify-center>
      <v-flex xs12 md6>
        <panel class="post" title="Create a new post">
          <v-form ref="form" v-model="valid" lazy-validation>
            <v-text-field
              v-model="title"
              label="title"
              required
            ></v-text-field>
            <!-- <v-text-field
              v-model="image"
              label="image"
              required
            ></v-text-field> -->
            <v-text-field
              v-model="text"
              label="text"
              multi-line
              required
            ></v-text-field>
            <v-btn
              :disabled="!valid"
              @click="submit"
              color="primary"
              dark
            >
              submit
            </v-btn>
            <v-btn :to="'/'">Cancel</v-btn>
          </v-form>
        </panel>
      </v-flex>
    </v-layout>
  </div>

</template>

<script>
import PostService from '../services/PostService'
export default {
  name: 'CreatePost',
  data: () => ({
    valid: true,
    title: '',
    image: '',
    text: ''
  }),
  methods: {
    submit () {
      if (this.$refs.form.validate()) {
        const newPost = {
          author: JSON.parse(localStorage.getItem('user')).username,
          title: this.title,
          image: this.image,
          text: this.text
        }
        PostService.createPost(newPost)
          .then(() => this.$router.push('/'))
          .catch((error) => console.log(error))
      }
    }
  }
}
</script>

<style scoped>
.create {
  height: 150px;
}
.post {
  background-color: rgb(220, 240, 243);
}
</style>
