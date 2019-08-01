<template>
  <nav>
    <ul>
      <li><nuxt-link to="/">-Index-</nuxt-link></li>
      <li><nuxt-link to="/about">-About-</nuxt-link></li>
      <li><nuxt-link to="/contact">-Contact-</nuxt-link></li>
    </ul>
  </nav>
</template>

<style>
nav {
  font-family: 'Noto Sans', 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 60px;
  color: #35495e;
  letter-spacing: 3px;
}
nav ul {
  display: -webkit-flex;
  display: flex;
  list-style: none;
}
nav ul li {
  width: calc(100%/3);
  margin: 6px;
  padding: 10px;
  border-radius: 5px;
  color: #fff;
}
nav ul li a {
  padding: 0px 80px;
  border-radius: 10px;
  color: #35495e;
  text-align: center;
  white-space: nowrap;
  text-decoration: none;
  transition: all  0.3s ease;
}
nav ul li :hover{
  color: #fff;
  background-color: #6eb1b0;
  text-decoration: none;
}

</style>
