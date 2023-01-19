<template>
  <div class="container">
    <section>
      <h2>Pages</h2>
      <div class="card">
        <h3>Keyboards</h3>
        <p>
          I enjoy tinkering with custom mechanical keyboards. From selecting all the parts to modding the stabilisers
          and building everything out. I put my favourite keyboards & configs on this website for those interested to
          see.
        </p>
        <nuxt-link to="/keyboards">
          <button title="See keyboards">
            See keyboards
          </button>
        </nuxt-link>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'IndexPage'
}
</script>
