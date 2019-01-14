<template>
    <div class="container">
    	<app-header 
    		:quotesQt="quotesQt" 
    		:addQuote="addQuote"
			:quotesMax="quotesMax"
    		></app-header>
    </div>
</template>

<script>
	import EventBus from './main.js'
	import Header from './components/header/Header.vue'

    export default {
    	created(){
    		EventBus.$on('addQuote', quote => this.quotes.push(quote))
    	},
    	data(){
    		return {
    			quotes: [],
    			quotesMax: 10,
    		}
    	},
    	components: {
    		'app-header': Header
    	},
    	methods:{
    		addQuote(quote){
    			EventBus.$emit('addQuote', quote)
    		}
    	},
    	watch:{
    		quotes(){
    			if(this.quotes.length > this.quotesMax){
    				alert('Max quotes quantity reached.')
    			}
    		}
    	},
    	computed:{
    		quotesQt(){
    			return this.quotes.length
    		}
    	}    
    }
</script>

<style>
</style>
