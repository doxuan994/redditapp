<template>
    <div id="app">
        <header>
            <h3>Subreddits</h3>
        </header>

        <Subreddits category="food"/>
        <Subreddits category="space"/>
        <Subreddits category="sport"/>
        <Subreddits category="art"/>
        <Subreddits category="funny"/>


        <Subreddits category="memes"/>


    </div>
</template>

<script>
import Subreddits from './components/Subreddits'

export default {
    name: 'App',
    components: {
        Subreddits
    }
}
</script>

<style>
    body {
        font-family: arial;
        color: #666666;
        background: #f4f4f4;
        margin: 0;
        padding: 0;
    }
    a {
        text-decoration: none;
    }
    header {
        background: coral;
        color: #fff;
        padding: 10px;
        text-align: center;
    }
</style>
