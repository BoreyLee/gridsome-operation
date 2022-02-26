<template>
  <Layout>
    <div class="container">
      <div class="contact-header">
        <h1 class="contact-title">Say hi!</h1>
        <p>
          Leave me a note with any questions you might have, I'll get back to
          you as soon as possible.
        </p>
      </div>
      <form
        name="contact"
        class="contact-form"
        v-on:submit.prevent="handleSubmit"
      >
        <div class="sender-info">
          <div>
            <label for="name" class="label">Your name</label>
            <input type="text" name="name" v-model="formData.name" />
          </div>
          <div>
            <label for="email" class="label">Your email</label>
            <input type="email" name="email" v-model="formData.email" />
          </div>
        </div>
        <div class="message">
          <label for="message" class="label">Message</label>
          <textarea name="message" v-model="formData.message"></textarea>
        </div>
        <button class="button" type="submit">Submit form</button>
      </form>
    </div>
  </Layout>
</template>

<script>
import axios from "axios";
export default {
  name: "ContactPage",
  metaInfo: {
    title: "Contact",
  },
  data() {
    return {
      formData: {
        name: "",
        email: "",
        message: "",
      },
    };
  },
  methods: {
    async handleSubmit() {
      try {
        await axios({
          url: `${this.GRIDSOME_API_URL}/contacts`,
          method: "POST",
          data: this.formData,
        });
        alert("提交成功！");
      } catch (error) {
        console.log(error);
        alert("提交失败！");
      }
    },
  },
};
</script>
