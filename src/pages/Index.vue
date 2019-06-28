<template>
  <Layout>

    <!-- Learn how to use images here: https://gridsome.org/docs/images -->
    <g-image alt="Example image" src="~/favicon.png" width="135" />

    <h1>James Bathgate</h1>

    <p>
      So I'm playing with Gridsome on Netlify and thinking of using it to build a new CV site.
    </p>

    <h2>Contact</h2>

    <form name="contact" method="POST" data-netlify-recaptcha="true" data-netlify="true">
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
</style>
