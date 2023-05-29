<script setup>
import { defineProps, defineEmits } from "vue";
const props = defineProps(["modalActive"]);

const emit = defineEmits(["close"]);

const handleCloseModal = () => {
  emit("close");
};
</script>

<template>
  <section>
    <transition name="modal-animation">
      <section class="modal" v-show="modalActive">
        <transition name="modal-animation-inner">
          <section class="modal-inner" v-show="modalActive">
            <i class="far fa-times-circle" @click="handleCloseModal"></i>
            <slot />
            <button class="close-modal" type="button" @click="handleCloseModal">
              Close modal
            </button>
          </section>
        </transition>
      </section>
    </transition>
  </section>
</template>

<style lang="scss" scoped>
.modal-animation-enter-active,
.modal-animation-leave-active {
  transition: opacity 0.3s cubic-bezier(0.52, 0.02, 0.19, 1.02);
}

.modal-animation-enter-from,
.modal-animation-leave-to {
  opacity: 0;
}

.modal-animation-inner-enter-active {
  transition: all 0.3s cubic-bezier(0.52, 0.02, 0.19, 1.02) 0.15s;
}

.modal-animation-inner-leave-active {
  transition: all 0.3s cubic-bezier(0.52, 0.02, 0.19, 1.02);
}

.modal-animation-inner-enter-from {
  opacity: 0;
  transform: scale(0.8);
}

.modal-animation-inner-leave-to {
  transform: scale(0.8);
}

.modal {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  width: 100vw;
  position: fixed;
  top: 0;
  left: 0;
  background-color: rgba(255, 255, 255, 0.9);

  .modal-inner {
    position: relative;
    max-width: 640px;
    width: 80%;
    background-color: #fff;
    padding: 64px 16px;
    text-align: center;

    .close-modal {
      background-color: crimson;
      color: #fff;
      margin-top: 0.5rem;

      &:focus,
      &:hover {
        background-color: rgb(250, 122, 96);
        color: #000;
      }
    }

    i {
      position: absolute;
      top: 15px;
      right: 15px;
      font-size: 2rem;
      cursor: pointer;

      &:focus,
      &:hover {
        color: crimson;
      }
    }

    button {
      border: 2px solid transparent;
      border-radius: 5px;
      padding: 20px 30px;
      border: none;
      font-size: 1rem;
      cursor: pointer;
      outline: none;
    }
  }
}
</style>
