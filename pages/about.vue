<template>
  <div class="main">
    <transition name="content_area">
      <div class="about">
        <div class="arrow"></div>
        <div class="ballon__area-01">
          <div @click="openModal(1)" class="balloon">PROFILE</div>
          <modal v-if="showModal == 1" @close="closeModal">
            <h3 slot="header">PROFILE</h3>
            <div slot="body">
              <p>Name:YopiNoji</p>
              <p>Address:Tokyo/Japan</p>
              <p>Occupation:Software Engineer</p>
            </div>
          </modal>
        </div>
        <div class="ballon__area-02">
          <div @click="openModal(2)" class="balloon">EDUCATION</div>
          <modal v-if="showModal == 2" @close="closeModal">
            <h3 slot="header">EDUCATION</h3>
            <div slot="body">
              <h4>2012~2017</h4>
              <p>YOKOHAMA CITY UNIVERSITY, Yokohama</p>
              <p>Bachelor of International Liberal Arts</p>
            </div>
          </modal>
        </div>
        <div class="ballon__area-03">
          <div @click="openModal(4)" class="balloon">LANGUAGE</div>
          <modal v-if="showModal == 4" @close="closeModal">
            <h3 slot="header">LANGUAGE</h3>
            <div slot="body">
              <h3>Language</h3>
              <li>JavaScript</li>
              <li>TypeScript</li>
              <li>PHP</li>
              <li>HTML5</li>
              <li>CSS3</li>
            </div>
          </modal>
        </div>

        <div class="ballon__area-04">
          <div @click="openModal(5)" class="balloon">OTHER SKILLS</div>
          <modal v-if="showModal == 5" @close="closeModal">
            <h3 slot="header">SKILLS</h3>
            <div slot="body">
              <h3>Framework</h3>
              <li>Vue.js</li>
              <li>Nuxt.js</li>
              <li>React.js</li>
              <li>Laravel</li>
              <h3>Middleware</h3>
              <li>Vuex</li>
              <li>GraphQl</li>
              <h3>Tool</h3>
              <li>Git</li>
              <h3>Service</h3>
              <li>AWS</li>
              <li>Firebase</li>
            </div>
          </modal>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
import Modal from '~/components/Modal.vue'
export default {
  layout: 'SideMenu',
  components: {
    Modal
  },
  data: () => ({
    showModal: 0,
    postItem: ''
  }),
  mounted() {},
  methods: {
    openModal(item) {
      this.showModal = item
    },
    closeModal() {
      this.showModal = false
    }
  }
}
</script>

<style>
.main {
  margin: 0 auto;
  height: 100vh;
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.links {
  padding-top: 15px;
}

.content_area-enter-active,
.content_area-leave-active,
.content_area-move {
  transition: opacity 1s, transform 1s;
}
.content_area-leave-active {
  position: absolute;
}
.content_area-enter {
  opacity: 0;
  transform: translateY(-20px);
}
.content_area-leave-to {
  opacity: 0;
  transform: translateY(20px);
}

/* about */
.about {
  height: 100%;
  width: 100%;
  overflow-x: hidden;
  overflow-y: scroll;
}

.ballon__area-01 {
  top: 5%;
  left: -20%;
  right: 0;
  position: absolute;
}

.ballon__area-02 {
  top: 25%;
  left: -20%;
  right: 0;
  position: absolute;
}

.ballon__area-03 {
  top: 45%;
  left: -20%;
  right: 0;
  position: absolute;
}

.ballon__area-04 {
  top: 65%;
  left: -20%;
  right: 0;
  position: absolute;
}

.ballon__area-05 {
  top: 85%;
  left: -20%;
  right: 0;
  position: absolute;
}

.arrow {
  transform: rotate(0deg);
  z-index: -1;
  position: absolute;
  top: -10%;
  width: 50%;
  height: 100%;
  right: 10%;
  border-left: 12px solid #000;
  border-bottom: 12px solid #000;
  box-sizing: border-box;

  animation-duration: 1s;
  animation-name: extend;
  animation-iteration-count: initial;
}

.arrow::after {
  content: '';
  position: absolute;
  bottom: -19px;
  right: -12px;
  border-top: 14px solid transparent;
  border-left: 14px solid #000;
  border-bottom: 14px solid transparent;
}

@keyframes extend {
  0% {
    transform: scaleY(0);
  }
  100% {
    transform: scaleY(1);
  }
}

.balloon {
  width: 120px;
  height: 80px;
  margin: 0 auto 40px;
  padding: 10px;
  background: #fff;
  border: 1px solid #000;
  text-align: center;
  animation-duration: 2s;
  animation-name: RightToLeft;
  animation-iteration-count: initial;
  position: relative;
  cursor: pointer;
  transition: 800ms ease all;
  outline: none;
}
.balloon:hover {
  color: #fff;
  background-color: #000;
}
.balloon:before,
.balloon:after {
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  height: 2px;
  width: 0;
  background: #fff;
  transition: 400ms ease all;
}
.balloon:after {
  right: inherit;
  top: inherit;
  left: 0;
  bottom: 0;
}
.balloon:hover:before,
.balloon:hover:after {
  width: 100%;
  transition: 800ms ease all;
}

@keyframes RightToLeft {
  0% {
    opacity: 0;
    transform: translateX(50px);
  }
  100% {
    opacity: 1;
    transform: translateX(0);
  }
}
</style>
