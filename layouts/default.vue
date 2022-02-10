<template>
  <div>
    <Header />
    <Nuxt />
  </div>
  <script>
    if (window.netlifyIdentity) {
      window.netlifyIdentity.on("init", (user) => {
        if (!user) {
          window.netlifyIdentity.on("login", () => {
            document.location.href = "/admin/";
          });
        }
      });
    }
  </script>
</template>

<script>
export default {
  head() {
    return {
      script: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        {
          src: "https://identity.netlify.com/v1/netlify-identity-widget.js",
        },
      ],
    };
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;

  font-family: sans-serif;
}
body {
  background-color: #eee;
}
a {
  text-decoration: none;
}
p {
  margin-bottom: 15px;
}
p:last-of-type {
  margin-bottom: 0px;
}
</style>
