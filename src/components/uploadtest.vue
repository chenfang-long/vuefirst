<template>
	<div>
		<!--<form enctype="multipart/form-data" method="post"  action="http://localhost:8085/upload">
			<input type="file" name="file" />
			<input type="submit" value="提交" />
		</form>-->
		测试修改

		test

		测试
		<input type="file" name="file" />
		<input type="submit" value="提交" v-on:click="upload"/>
	</div>
</template>

<script>
	export default {
		name: 'uploadtest',
		methods:{
			upload:function(){
				var fomdata = new FormData();//相当于表单
				fomdata.append("file",document.querySelector("input[name=file]").files[0]);
				
				var config={
					headers:{
						"Content-type":"multipart/from-data"
					}
				}
				
				
				this.$http.post("http://localhost:8085/upload",fomdata,config).then(
					function(result){
						console.log(result);
						console.log(result.bodyText)
						alert("文件上传成功");
						this.$router.go(0);
					},
					function(error){
						 console.log(error.body.message)
					}
				)
			}
		}
	}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	/*只作用于当前组件*/
</style>