<script setup>
import { onMounted, ref } from 'vue';

// import { faker } from '@faker-js/faker';
import { ElTable, ElTableColumn } from 'element-plus';

const projects = ref([]);

// 生成假的项目数据
const generateFakeData = () => {
  const data = [];
  for (let i = 0; i < 10; i++) {
    data.push({
      id: i + 1,
      // name: faker.company.name(),
      // description: faker.lorem.sentence(),
      // repositoryUrl: faker.internet.url(),
      // serverHost: faker.internet.ip(),
      // accessUrl: faker.internet.url(),
    });
  }
  return data;
};

onMounted(() => {
  projects.value = generateFakeData();
});

const editProject = () => {
  // console.log('编辑项目', project);
};

const deleteProject = () => {
  // console.log('删除项目 ID', id);
};
</script>

<template>
  <ElTable :data="projects" style="width: 100%">
    <ElTableColumn label="ID" prop="id" width="50" />
    <ElTableColumn label="项目名称" prop="name" />
    <ElTableColumn label="描述" prop="description" />
    <ElTableColumn label="代码仓库" prop="repositoryUrl" />
    <ElTableColumn label="服务器地址" prop="serverHost" />
    <ElTableColumn label="访问地址" prop="accessUrl" />
    <ElTableColumn label="操作">
      <template #default="scope">
        <el-button @click="editProject(scope.row)">编辑</el-button>
        <el-button type="danger" @click="deleteProject(scope.row.id)">
          删除
        </el-button>
      </template>
    </ElTableColumn>
  </ElTable>
</template>
