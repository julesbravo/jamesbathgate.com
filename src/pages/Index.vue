<template>
  <Layout>

  <!-- Learn how to use images here: https://gridsome.org/docs/images -->
  <g-image alt="Example image" src="~/favicon.png" width="135" />

  <h1>James Bathgate</h1>

  <p>
    So I'm playing with Gridsome on Netlify and thinking of using it to build a new CV site.
  </p>

  <h2>Contact</h2>
  <h3 class="error">This form doesn't actually work, yet. Reach out to me on LinkedIn instead.</h3>
  <form name="contact" method="POST" data-netlify-recaptcha="true" data-netlify="true" action="/success/" v-on:submit.prevent="handleSubmit">
    <input type="hidden" name="form-name" value="contact" />
    <p>
      <label>Email: <input type="text" name="name" /></label>
    </p>
    <p>
      <label>Message: <textarea name="message" class="message"></textarea></label>
    </p>
    <div data-netlify-recaptcha="true"></div>
    <p>
      <button type="submit">Send</button>
    </p>
  </form>

  <p class="home-links">
    <a href="https://gridsome.org/docs" target="_blank" rel="noopener">Gridsome Docs</a>
    <a href="https://github.com/gridsome/gridsome" target="_blank" rel="noopener">Gridsome GitHub</a>
    <a href="https://www.netlify.com" target="_blank" rel="noopener">Netlify</a>
  </p>

  </Layout>
</template>

<script>
export default {
  metaInfo: {
  title: 'Home'
  },
  data() {
    return {
      formData: {},
    }
  },
  methods: {
    encode(data) {
      return Object.keys(data)
        .map(key => encodeURIComponent(key) + '=' + encodeURIComponent(data[key]))
        .join('&')
    },
    handleSubmit(e) {
      fetch('/', {
        method: 'POST',
        headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
        body: this.encode({
          'form-name': e.target.getAttribute('name'),
          ...this.formData,
        }),
      })
      .then(() => this.$router.push('/success'))
      .catch(error => alert(error))
    }
  }
}
</script>

<style>
.home-links a {
  margin-right: 1rem;
}

form textarea.message {
  width: 100%;
  height: 200px;
}

h3.error {
  color: red;
}
</style>
