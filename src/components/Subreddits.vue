<template>
    <div class="subreddits container">
        <h2>{{category | capitalize}}</h2>
        <ul class="item-list">
            <li v-for="post in subreddits">
                <Subreddit v-bind:item="post" />
            </li>
        </ul>
    </div>
</template>

<script>

import Subreddit from './Subreddit'


export default {
    name: 'Subreddits',
    components: {
        Subreddit
    },
    props: ['category'],
    data () {
        return {
            subreddits: [

            ]
        }
    },
    filters: {
        capitalize: function(value) {
            if(!value) return '';
            value = value.toString();
            return value.charAt(0).toUpperCase() + value.slice(1);
        }
    },
    created: function() {
        this.$http.get('https://www.reddit.com/r/' + this.category + '/top.json?limit=5').then((response) => {
            this.subreddits = response.data.data.children;
        });
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .container {
        max-width: 600px;
        margin: 30px auto;
        background: #fff;
        box-shadow: 0 0 3px #ccc;
    }
    .subreddits {
        min-width: 400px;
        padding: 25px 45px;
    }
    .subreddits h2 {
        font-size: 20px;
        margin-bottom: 10px;
        margin-top: 0;
    }
    .subreddits .item-list {
        border-top: 1px solid #ccc;
        padding-top: 20px;
        list-style: none;
    }
</style>
