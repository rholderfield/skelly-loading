<template>
  <div class="hello">
    <div id="card-template" v-for="post in data" :key="post.id">
      <a class="card" id="card-link" target="_blank" :href="post.link">
        <div class="card__header">
          <div>
            <img class="header__img skeleton" id="logo-img" alt="logo-img" :src="post.logoImage" />
          </div>
          <h3 class="card__header header__title" id="card-title">
            <div class="skeleton skeleton-text">{{ post.title }}</div>
            <div class="skeleton skeleton-text"></div>
          </h3>
        </div>

        <div class="card__body">
          <div class="card__body body__text" id="card-details">
            <div class="skeleton skeleton-text skeleton-text__body">{{ post.details }}</div>
          </div>

          <div class="card__body body__img">
            <img class="skeleton" alt="cover-img" id="cover-img" :src="post.coverImage" />
          </div>
        </div>

        <div class="card__footer" id="card-footer">
          <div class="skeleton skeleton-text skeleton-footer"></div>
        </div>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      data: [],
    };
  },
  mounted() {
    this.getData();
  },
  methods: {
    async getData() {
      fetch("dataTest.json")
        .then((response) => response.json())
        .then((posts) => {
          posts.forEach((post) => {
            this.data.push(post);
          });
        });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.card {
  background-color: #f5f8fc;
  padding: 0.5rem;
  border-radius: 1rem;
  border: 1px solid rgba(82, 88, 102, 0.2);
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  -ms-flex-direction: column;
  flex-direction: column;
  -ms-flex-pack: distribute;
  justify-content: space-around;
  width: 330px;
  height: auto;
  -webkit-transition: all 0.2s ease;
  transition: all 0.2s ease;
  margin: 2rem;
}

.card__header {
  margin-bottom: 1rem;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  -ms-flex-direction: column;
  flex-direction: column;
  margin: 0.5rem 0 0.5rem 0.5rem;
}

.card__header .header__img {
  height: 2rem;
  width: 2rem;
  -o-object-fit: cover;
  object-fit: cover;
  border-radius: 50%;
}

.card__header .header__title {
  font-size: 1.0625rem;
  line-height: 1.375rem;
  color: #0e1217;
  font-weight: 700;
  margin: 0.5rem;
}

.card__body {
  margin: 0 0.5rem;
}

.card__body .body__text {
  color: #525866;
  font-size: 0.8125rem;
}

.card__body .body__img {
  height: 10rem;
  margin: 0.5rem 0;
}

.card__body .body__img img {
  width: 100%;
  height: 100%;
  -o-object-fit: cover;
  object-fit: cover;
  margin: auto;
  border-radius: 0.75rem;
}

.card__footer {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -ms-flex-pack: distribute;
  justify-content: space-around;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  margin: 0.5rem;
}

.card:hover {
  border-color: rgba(82, 88, 102, 0.4);
}

.skeleton {
  -webkit-animation: skeleton-loading 0.5s linear 2 alternate;
  animation: skeleton-loading 0.5s linear 2 alternate;
}

@-webkit-keyframes skeleton-loading {
  0% {
    background-color: #c2cfd6;
  }
  100% {
    background-color: #f0f3f5;
  }
}

@keyframes skeleton-loading {
  0% {
    background-color: #c2cfd6;
  }
  100% {
    background-color: #f0f3f5;
  }
}

.skeleton-text {
  width: 100%;
  height: 0.7rem;
  margin-bottom: 0.5rem;
  border-radius: 0.25rem;
}

.skeleton-text__body {
  width: 75%;
}

.skeleton-footer {
  width: 30%;
}
</style>
