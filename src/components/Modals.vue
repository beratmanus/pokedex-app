<template>
  <div class="modal-backdrop">
    <div class="modal w-full absolute bottom-0 p-4">
      <header class="flex my-4 justify-between">
        <slot name="header">
          <h2>Sorteren op</h2>
        </slot>
        <button
          type="button"
          class=""
          @click="close"
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
  <path stroke-linecap="round" stroke-linejoin="round" d="M10 14l2-2m0 0l2-2m-2 2l-2-2m2 2l2 2m7-2a9 9 0 11-18 0 9 9 0 0118 0z" />
</svg>
        </button>
      </header>
      <section class=" mb-2 text-left bg-gray-200 p-3 rounded-xl text-black">
        <slot name="body">
          Alfabetsich oplopend
        </slot>
       </section>
      <section class=" mb-2 text-left bg-gray-200 p-3 rounded-xl text-black">
        <slot name="body">
          Alfabetsich aflopend
        </slot>
       </section>
      <section class=" mb-2 text-left bg-gray-200 p-3 rounded-xl text-black">
        <slot name="body">
          Numeriek oplopend
        </slot>
       </section>
      <section class="mb-3 text-left bg-gray-200 p-3 rounded-xl text-black">
        <slot name="body">
          Numeriek aflopend
        </slot>
       </section>

      <footer class="modal-footer">
        <button
          type="button"
          class="bg-black text-white m-auto w-full py-3 rounded-full text-lg font-bold"
          @click="close"
        >
          Toepassen
        </button>
      </footer>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Modal',
    methods: {
      close() {
        this.$emit('close');
      },
    },
  };
</script>
<style>
  .modal-backdrop {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: rgba(0, 0, 0, 0.3);
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .modal {
    background: #FFFFFF;
    box-shadow: 2px 2px 20px 1px;
    overflow-x: auto;
    display: flex;
    flex-direction: column;
  }

  
</style>
