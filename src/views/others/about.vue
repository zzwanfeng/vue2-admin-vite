<template>
  <div page-card>
    <el-card class="box-card" header="" :body-style="{ fontSize: '15px' }" shadow="hover">
      <template #header>
        <span class="title">vue2-admin-vite ✨✨✨  by zzwanfeng</span>
      </template>

      <div>
        VAdmin Plus 是一款基于Vue2 + Element + Vite
        等技术栈搭建的通用后台系统模板。
      </div>
    </el-card>

    <el-card class="box-card" header="" :body-style="{ fontSize: '15px' }" shadow="hover">
      <template #header>
        <span class="title">生产环境依赖 🍞🍞🍞</span>
      </template>

      <el-descriptions :column="3" border size="large">
        <el-descriptions-item
          v-for="item in DependenciesArr"
          :key="item.name"
          label-align="center"
          align="center"
          width="150px"
          :label="item.name"
        >
          {{ item.version }}
        </el-descriptions-item>
      </el-descriptions>
    </el-card>

    <el-card class="box-card" header="" :body-style="{ fontSize: '15px' }" shadow="hover">
      <template #header>
        <span class="title">开发环境依赖 📦︎ 📦︎ 📦︎</span>
      </template>

      <el-descriptions :column="3" border size="large">
        <el-descriptions-item
          v-for="item in DevDependenciesArr"
          :key="item.name"
          label-align="center"
          align="center"
          width="150px"
          :label="item.name"
        >
          {{ item.version }}
        </el-descriptions-item>
      </el-descriptions>
    </el-card>
  </div>
</template>

<script setup>
import ProjectConfigJson from '../../../package.json'

const { dependencies, devDependencies } = ProjectConfigJson

const DependenciesArr = []
const DevDependenciesArr = []

Object.keys(dependencies).forEach((key) => {
  const dependenciesObj = { name: '', version: '' }
  dependenciesObj.name = key
  dependenciesObj.version = dependencies[key]
  DependenciesArr.push(dependenciesObj)
})

Object.keys(devDependencies).forEach((key) => {
  const dependenciesObj = { name: '', version: '' }
  dependenciesObj.name = key
  dependenciesObj.version = devDependencies[key]
  DevDependenciesArr.push(dependenciesObj)
})

</script>

<style scoped lang="scss">
.box-card:not(:last-child) {
  margin-bottom: 1.5rem;
}

.title {
  font-size: 1.2rem;
  line-height: 1;
  font-weight: 500;
}
</style>
