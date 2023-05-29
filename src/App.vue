<template>
  <h1>Reusable Modal Component</h1>
  <ReusableModal @close="toggleModal" :modalActive="modalActive">
    <section class="modal-content">
      <h2>This is a modal content</h2>
      <p>Modal paragraph</p>
    </section>
  </ReusableModal>
  <button
    class="open-modal"
    v-show="!modalActive"
    type="button"
    @click="toggleModal"
  >
    Open Modal
  </button>
</template>

<script>
import { ref } from "vue";
import ReusableModal from "@/components/ReusableModal.vue";
export default {
  name: "App",
  components: {
    ReusableModal,
  },
  setup() {
    const modalActive = ref(false);

    const toggleModal = () => {
      modalActive.value = !modalActive.value;
    };

    return {
      modalActive,
      toggleModal,
    };
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Karla:wght@300;400&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Karla", sans-serif;
  font-size: 16px;
}

#app {
  background-color: rgba(0, 176, 234, 0.5);
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  h1 {
    margin-bottom: 0.5rem;
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

  .open-modal {
    background-color: green;
    color: #fff;

    &:focus,
    &:hover {
      border: 2px solid #fff;
      background-color: rgb(77, 116, 77);
      margin: -2px;
    }
  }

  .modal-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    h2,
    p {
      margin-bottom: 0.5rem;
    }

    h1 {
      font-size: 1.8rem;
    }

    h2 {
      font-size: 1.5rem;
    }

    p {
      font-size: 1.2rem;
    }
  }
}
</style>
