<template>
  <div class="layout sticky-header">
    <header class="header sticky">
      <div class="container">
        <div class="left">
          <g-link class="home-link active" to="/">
            <img src="../../static/img/logo.svg" class="logo" />
          </g-link>
        </div>
        <nav class="nav right">
          <g-link class="nav__link" to="/journal">Journal</g-link>
          <g-link class="nav__link" to="/contact">Say Hi!</g-link>
        </nav>
      </div>
    </header>
    <slot />
    <footer class="footer">
      <div class="container">
        <span>Copyright © 2022</span>
      </div>
    </footer>
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<style scoped>
.layout {
  margin: 0 auto;
}
.layout {
  padding: 0;
}
.layout.sticky-header {
  padding: 6rem 0 0;
}

.home-link {
  text-decoration: none;
}


.logo {
  height: 1.5rem;
}

.header {
  margin-bottom: 20px;
  position: relative;
  height: 6rem;
  z-index: 10;
}
.header.sticky {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
}
.header .container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 100%;
}

.nav__link {
  margin-left: 20px;
  font-size: 0.9rem;
  font-weight: 600;
  text-decoration: none;
  margin-top: 4px;
  margin-right: 3rem;
  padding-bottom: 4px;
  border-bottom: 1px solid;
  border-color: transparent;
  transition: border 0.15s;
}

.nav__link:last-of-type {
  margin: 0;
}

.nav__link.active,
.nav__link:hover {
  border-color: inherit;
}
.footer {
  font-size: 0.8rem;
  padding: 6rem 0;
}
</style>
