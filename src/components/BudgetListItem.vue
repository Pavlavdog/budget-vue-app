<template>
	<div>
		<div class="list-item" v-for="item in list" :key="item.id">
			<span class="budget-comment">{{ item.comment}} </span>
			<span :class="['budget-value', classColorNumber(item.type)]"> {{ item.value}} <i :class="classIcon(item.type)"></i></span>
			<el-button type="danger" @click="deleteItem(item.id)">Delete</el-button>
		</div>
	</div>
</template>

<script>
export default {
	name: 'BudgetListItem',
  props: {
    list: {
      type: Object,
      default: () => ({}),
    }
  },
  methods: {
    deleteItem(id) {
      this.$emit('deleteListItem', id);
      this.centerDialogVisible = false;
		},
		classIcon(itemType) {
			return {
				'el-icon-top': itemType === 'INCOME',
				'el-icon-bottom': itemType === 'OUTCOME',
			}
		},
		classColorNumber(itemType) {
			return {
				'green': itemType === 'INCOME',
				'red': itemType === 'OUTCOME',
			}
		},
		onCloseItem(status) {
			this.centerDialogVisible = status;
		}
  }
}
</script>

<style scoped>
  .list-item {
    display: flex;
    align-items: center;
    padding: 10px 15px;
  }

  .budget-value {
    font-weight: bold;
    margin-left: auto;
    margin-right: 20px;
  }
	.green {
		color: green;
	}
	.red {
		color: red;
	}
</style>>
