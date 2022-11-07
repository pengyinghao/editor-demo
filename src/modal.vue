<template>
  <a-modal
    v-model:visible="visible"
    width="800px"
    title="测试"
    @cancel="onCancel()"
    @ok="onCancel"
  >
    <WangEditor v-model="content" show-tool-bar />
  </a-modal>
</template>
<script lang="ts" setup name="CreateNotice">
import WangEditor from "./components/WangEditor.vue";
import { ref } from "vue";

const content = ref("");
const visible = ref(false);

const onCancel = () => {
  content.value = "";
  visible.value = false;
};
const showModal = (type: "add" | "edit") => {
  visible.value = true;
  if (type === "edit") {
    content.value = "<p>1</p><p>2</p><p>3</p";
  }
};

defineExpose({
  showModal,
});
</script>
