<template>
  <transition name="modal">
    <div
      v-if="visible"
      @click="$modal.hide(name)"
      class="app-modal"
    >
      <div class="app-modal__inner">
        <div>
          <button @click="$modal.hide(name)" class="btn btn-warning">Close</button>
        </div>
        <slot name="body" :params="params"/>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  props: {
    name: {
      required: true,
      type: String
    }
  },

  data () {
    return {
      visible: false,
      params: {}
    }
  },

  methods: {
    setVisible () {
      this.visible = true
    },

    setHidden () {
      this.visible = false
    }
  },

  beforeMount () {
    this.$modal.$event.$on('show', (modal, params) => {
      if (this.name === modal) {
        this.params = params

        if (!this.$listeners['before-open']) {
          this.setVisible()
          return
        }

        this.$emit('before-open', () => {
          this.setVisible()
        })
      }
    })

    this.$modal.$event.$on('hide', (modal) => {
      if (this.name === modal) this.setHidden()
    })
  },

  mounted () {
    document.addEventListener('keydown', (e) => {
      if (this.visible && e.keyCode === 27) this.visible = false
    })
  }
}
</script>

<style lang="scss">
.app-modal {
  overflow-y: auto;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 9999;
  width: 100%;
  height: 100%;
  font-size: 0;
  text-align: center;
  background-color: #141420;

  &::before {
    content: '';
    height: 100%;
  }

  &::before,
  &__inner {
    display: inline-block;
    vertical-align: middle;
  }
}

.app-modal__inner {
  width: 90%;
  max-width: 500px;
  padding: 30px;
  margin: 40px 0;
  font-size: 1rem;
  background-color: #fff;
}

.modal-enter,
.modal-leave-active { opacity: 0; }

.modal-enter-active,
.modal-leave-active { transition-duration: .2s; }
</style>
