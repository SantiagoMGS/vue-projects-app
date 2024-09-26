<template>
  <!-- Open the modal using ID.showModal() method -->
  <dialog class="modal" :open="open">
    <div class="modal-box">
      <!-- Titulo -->
      <div class="border-b border-blue-500">
        <!-- HEADER -->
        <slot name="header" />
      </div>

      <!-- Contenido -->
      <div class="my-5">
        <slot name="body" />
      </div>

      <div class="modal-action">
        <slot name="actions" />
      </div>
    </div>
  </dialog>
  <div
    v-if="open"
    class="modal-backdrop fixed top-0 left-0 z-10 bg-black opacity-50 w-screen h-screen"
  ></div>
</template>

<script setup lang="ts">
interface Props {
  open?: boolean;
}

withDefaults(defineProps<Props>(), {
  open: false,
});
</script>
