<template>
  <div class="budget-list-wrap">
    <el-card :header="header">
     <template v-if="!isEmpty">
       <BudgetListItem :list="list" @deleteListItem="onDeleteListItem"/>
     </template>
     <el-alert v-else type="info" :title="emptyTitle" :closable=false />
    </el-card>
  </div>
</template>

<script>
import BudgetListItem from './BudgetListItem';

export default {
  name: 'BudgetList',
  components: {
    BudgetListItem
  },
  props: {
    list: {
      type: Object,
      default: () => ({}),
    }
  },
  data: () => ({
    header: 'Budget List',
    emptyTitle: 'Empty List!',
  }),
  computed: {
    isEmpty() {
      return !Object.keys(this.list).length;
    }
  },
  methods: {
    onDeleteListItem(id) {
      this.$emit('deleteItem', id);
    }
  }
}
</script>

<style scoped>
  .budget-list-wrap {
    max-width: 500px;
    margin: auto;
  }
</style>>
