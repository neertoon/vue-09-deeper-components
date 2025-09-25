<template>
  <div>
    <the-header></the-header>
    <badge-list></badge-list>
    <user-info
      :full-name="activeUser.name"
      :info-text="activeUser.description"
      :role="activeUser.role"
    ></user-info>
    <course-goals>
      <template #default="slotProps">
        <h2>{{ slotProps.item }}</h2>
        <p>{{ slotProps['another-prop'] }}</p>
      </template>
    </course-goals>

    <button @click="setSelectComponent('active-goals')">Active Goals</button>
    <button @click="setSelectComponent('manage-goals')">Managed Goals</button>
    <!--
    <active-goals v-if="selectedComponent == 'active-goals'"></active-goals>
    <manage-goals v-if="selectedComponent == 'manage-goals'"></manage-goals>
    -->

    <component :is="selectedComponent">

    </component>
  </div>
</template>

<script>
import CourseGoals from "./components/CourseGoals.vue";
import ActiveGoals from "./components/ActiveGoals.vue";
import ManageGoals from "./components/ManageGoals.vue";


export default {
  components: {
    CourseGoals,
    ActiveGoals,
    ManageGoals,
  },
  data() {
    return {
      selectedComponent: 'active-goals',
      activeUser: {
        name: 'Maximilian Schwarzmüller',
        description: 'Site owner and admin',
        role: 'admin',
      },
    };
  },
  methods: {
    setSelectComponent(componentName) {
      this.selectedComponent = componentName;
    }
  }
};
</script>

<style>
html {
  font-family: sans-serif;
}

body {
  margin: 0;
}
</style>