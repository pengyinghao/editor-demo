<script setup lang="ts">
import Modal from "./modal.vue";
import { ref } from "vue";
const refModal = ref<InstanceType<typeof Modal>>();
const onShowModal = (type: "add" | "edit") => {
  refModal.value?.showModal(type);
};
</script>
<template>
  <Modal ref="refModal" />
  <a-button type="primary" @click="onShowModal('add')">新增</a-button>
  <a-button type="primary" @click="onShowModal('edit')">修改</a-button>
</template>
<style scoped></style>
