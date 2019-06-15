<template>
    <div class="subreddit">
        <a v-bind:href="makeUrl(item.data.permalink)" v-bind:style="makeImage(item.data.thumbnail)" target="_blank" class="thumbnail"></a>
        <div class="details">
            <a :href="makeUrl(item.data.permalink)" :title="item.data.title" target="_blank" class="title">
                {{item.data.title | truncate}}
            </a>
            <div class="stats">
                <i class="far fa-thumbs-up"></i>{{item.data.score}}
                <i class="far fa-comment-alt"></i>{{item.data.num_comments}}
            </div>
        </div>

    </div>
</template>

<script>
export default {
    name: 'Subreddit',
    props: ['item'],
    data () {
        return {

        }
    },
    methods: {
        makeUrl: function(permalink) {
            return 'https://www.reddit.com/' + permalink;
        },
        makeImage: function(img) {
            return 'background-image: url('+img+')';
        }
    },
    filters: {
        truncate: function(value) {
            let length = 30;
            if (value.length <= length) {
                return value;
            } else {
                return value.substring(0, length) + '...';
            }
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

    .subreddit {
        display: flex;
    }

    .thumbnail {
        display: block;
        flex: 0 0 65px;
        height: 65px;
        background-repeat: no-repeat;
        background-size: cover;
        background-position: center;
        margin-right: 12px;
        border-radius: 5px;
    }

    .subreddit .details .title {
        font-size: 15px;
        margin-bottom: 5px;
        color: steelblue;
    }

    .subreddit .stats {
        font-size: 12px;
        margin-right: 4px;
        margin-top: 7px;
        display: inline-block;
        color: #ccc;
    }

    .subreddit .stats i {
        font-size: 10px;
        margin-right: 2px;
    }

</style>
