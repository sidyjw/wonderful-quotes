<template>
	<header>
		<h1 class="h1">Quotes Add</h1>
		<div class="progress">
  			<div class="progress-bar" role="progressbar" :style="progressbarWidth">
    			<span class="" @click="addQuote(1)">{{quotesQt}}/{{quotesMax}}</span>
  			</div>
		</div>
	</header>
</template>

<script>
	export default{
		props: {
			quotesQt: Number,
			quotesMax: Number,
			addQuote: Function
		},
		computed: {
			progressbarWidth(){
				const result = (this.quotesQt / this.quotesMax) * 100 
				return {
					width: `${result}%`
				}
			}
		}
	}
</script>