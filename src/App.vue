<template>
    <div class="container">
    	<app-header 
    		:quotesQt="quotesQt" 
    		:addQuote="addQuote"
			:quotesMax="quotesMax"
    		></app-header>
    	<app-add-quote :addQuote="addQuote"></app-add-quote>
    </div>
</template>

<script>
	import EventBus from './main.js'
	import Header from './components/header/Header.vue'
	import AddQuote from './components/quotes/AddQuote.vue'

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
    		'app-header': Header,
    		'app-add-quote': AddQuote
    	},
    	methods:{
    		addQuote(quote){
    			if(this.quotes.length === this.quotesMax){
    				return alert('Max quotes quantity reached.')
    			}
    			EventBus.$emit('addQuote', quote)
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
