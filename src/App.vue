<template>
    <div class="container">
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
        <app-add-quote @quoteAdded="newQuote"></app-add-quote>
        <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">Info: Click on a Quote to delete it!</div>
            </div>
        </div>
    </div>
</template>

<script>
    import QuoteGrid from './Components/QuoteGrid.vue'
    import AddQuote from './Components/AddQuote.vue'
    import Header from './Components/Header.vue'

    export default {
        data: function() {
            return {
                quotes: ['First Quote'],
                maxQuotes: 10
            }
        },
        methods: {
          newQuote(quote) {
              if (this.quotes.length >= this.maxQuotes) {
                  return alert('Please delete quotes first');
              }
              this.quotes.push(quote);
          },
          deleteQuote(index) {
              this.quotes.splice(index, 1);
          }
        },
        components: {
            appQuoteGrid: QuoteGrid,
            appAddQuote: AddQuote,
            appHeader: Header
        },
    }
</script>

<style>
</style>
