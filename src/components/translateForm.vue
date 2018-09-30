<template>
	<div class="row" id="translateForm">
		<div class="col-md-6 col-md-offset-3">
			<form id="transForm" class="well form-inline" v-on:submit="submitForm">
				<input class="form-control" type="text" placeholder="请输入翻译内容" v-model="translateText">
				<select class="form-control" v-model="code">
					<option value="zh">Chinese</option>
					<option value="en">English</option>
					<option value="ko">Korean</option>
					<option value="fr">French</option>
					<option value="ro">Romanian</option>
					<option value="de">German</option>
				</select>
				<input class="btn btn-primary" type="submit" value="翻译">
			</form>			
		</div>
	</div>
</template>

<script>
	export default {
		name: 'translateForm',
		data: function () {
			return {
				code: "",
				translateText: ""
			}
		},
		methods: {
			submitForm(e) {
				this.$emit('submitForm', this.translateText, this.code);	
				e.preventDefault();
			}
		},
		created() {
			this.code = 'en'
		}
	}
</script>

<style>
	#transForm{
		border: 1px #ccc solid;
		border-radius: 10px
	}
</style>