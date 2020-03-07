<template>
	<div>
		<el-dialog
				title="title"
				:visible.sync="centerDialogVisible"
				width="30%"
				center>
			<span>Are you sure that you want to delete the record? {{title2}}</span>
			<span slot="footer" class="dialog-footer">
				<el-button @click="closeDialog(false)">Cancel</el-button>
				<el-button type="primary" @click="deleteItem(id)">Confirm</el-button>
			</span>
		</el-dialog>
	</div>
</template>

<script>
export default {
	name: 'BudgetListDialog',
  props: {
    id: {
      type: Number,
      default: 0,
		},
		centerDialogVisible: {
      type: Boolean,
      default: false,
		}
  },
  methods: {
    deleteItem(id) {
			console.log("ENNNNNN: " + id);
      this.$emit('deleteListItemDialog', id);
      this.centerDialogVisible = false;
		},
		closeDialog(status) {
			this.$emit('closeDialog', status);
		}
  }
}
</script>

<style scoped>
</style>>
