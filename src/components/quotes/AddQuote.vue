<template>
	<div>
		<div class="form-group">
  			<label for="comment">Quote</label>
  			<textarea 
  				v-model="registredQuote" 
  				class="form-control" 
  				rows="5" 
  				id="comment"></textarea>
  			<button class="btn btn-primary" @click="registerQuote">Add Quote</button>
		</div>		
	</div>
</template>

<script>
	export default {
		props: ['addQuote'],
		data(){
			return {
				registredQuote: '',
			}
		},
		methods: {
			registerQuote(){
				const isBlank = /^\s*$/;
				if(isBlank.test(this.registredQuote)){
					return alert('Please, insert some text.');
				}
				this.addQuote(this.registredQuote);
				this.registredQuote = '';
			}
		}
	}
</script>

<style scoped>
	.form-group{
		padding: 0 10%;
		display: flex;
		flex-flow: column;
		align-items: center;
	}
	label{
		align-self: flex-start;
	}
	button{
		margin-top: 20px;
		width: 25%;
	} 
</style>
