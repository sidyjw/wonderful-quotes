<template>
    <div class="container">
    	<app-header 
    		:quotesQt="quotesQt" 
    		:addQuote="addQuote"
			:quotesMax="quotesMax"
    		></app-header>
    	<app-add-quote :addQuote="addQuote"></app-add-quote>
    	<app-quotes-area>
			<div v-for="(quote, index) in quotes" @click="deleteQuote(index)">{{quote}}</div>
    	</app-quotes-area>
    	<div class="alert alert-info text-center">
  			<strong>Info:</strong> Click on a Quote to delete it.
		</div>
    </div>
</template>

<script>
	import EventBus from './main.js'
	import Header from './components/header/Header.vue'
	import AddQuote from './components/quotes/AddQuote.vue'
	import QuotesArea from './components/quotes/QuotesArea.vue'

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
    		'app-add-quote': AddQuote,
    		'app-quotes-area': QuotesArea
    	},
    	methods:{
    		addQuote(quote){
    			if(this.quotes.length === this.quotesMax){
    				return alert('Max quotes quantity reached.')
    			}
    			EventBus.$emit('addQuote', quote)
    		},
    		deleteQuote(index){
    			this.quotes.splice(index, 1);
    		}
    	},
    	computed:{
    		quotesQt(){
    			return this.quotes.length
    		}
    	}    
    }
</script>


