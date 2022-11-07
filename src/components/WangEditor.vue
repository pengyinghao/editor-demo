<template>

    <Toolbar
      v-if="showToolBar"
      :editor="editorRef"
      :default-config="toolbarConfig"
      :mode="mode"
    />
    <Editor
      :style="{ height: `${height}px` }"
      :default-config="editorConfig"
      :mode="mode"
      v-bind="$attrs"
      @on-created="handleCreated"
    />
</template>
<script lang="ts" setup name="WangEditor">
import { shallowRef } from "vue";
import "@wangeditor/editor/dist/css/style.css";
import { IEditorConfig, IToolbarConfig, IDomEditor } from "@wangeditor/editor";
import { Editor, Toolbar } from "@wangeditor/editor-for-vue";

interface Props {
  /** 编辑器高度 */
  height?: number;
  /** 是否显示toolbar */
  showToolBar: boolean;
}
withDefaults(defineProps<Props>(), {
  modelValue: "",
  height: 300,
  showToolBar: false,
});

const mode = "default";
const toolbarConfig: Partial<IToolbarConfig> = {
  excludeKeys: ["fullScreen"],
};

const editorConfig: Partial<IEditorConfig> = { placeholder: "请输入内容..." };

const editorRef = shallowRef();
const handleCreated = (editor: IDomEditor) => {
  editorRef.value = editor;
};
</script>
