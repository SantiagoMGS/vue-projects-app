<template>
  <BreadCrumbs :name="project?.name ?? 'No name'"></BreadCrumbs>
</template>

<script setup lang="ts">
import BreadCrumbs from '@/modules/common/components/BreadCrumbs.vue';
import { useProjectsStore } from '../store/projects.store';
import { ref, watch } from 'vue';
import type { Project } from '../interfaces/project.interface';
interface Props {
  id: string;
}

const props = defineProps<Props>();

const projectStore = useProjectsStore();

const project = ref<Project | null>();

watch(
  () => props.id,
  () => {
    project.value = projectStore.projectList.find((project) => project.id === props.id) ?? null;
  },
  {
    immediate: true,
  },
);
</script>
