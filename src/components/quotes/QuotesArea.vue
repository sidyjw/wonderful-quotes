<template>
	<main>
		<slot></slot>
	</main>
</template>

<style scoped>
	main{
		margin-top: 20px;
		display: flex;
		flex-flow: wrap;
		justify-content: center;
		align-items: flex-start;
	}
	div{
		font-family: 'Arizonia';
		font-size: 30px;
		max-width: 30%;
		padding: 10px 20px; 
		border: 1px solid grey;
		border-radius: 5px;
		margin: 10px 15px;
		word-break: break-word;
	}
</style>