<template>
    <div class="card">
        <h3 v-if="info.title">{{info.title}}</h3>
        <h3 v-else>{{info.name}}</h3>
        <h4>{{info.original_title ? info.original_title : info.original_name}}</h4>
        <p>{{vote}}</p>
        <span v-for="n in 5" :key="n">{{ n }} </span>
        <p>
            <img v-if="existFlag(info.original_language)" :src="require(`../../assets/flags/${info.original_language}.png`)" :alt="info.original_language">
            <img width="30" v-else src="../../assets/flags/pace.png" alt="Pace">
        </p>
    </div>
</template>

<script>
export default {
    name: 'BaseCard',
    props: {
        info: Object,
    },
    data() {
        return {
            flagsAviable: [
                'en'
            ]
        }
    },
    computed: {
        vote() {
            return Math.ceil(this.info.vote_average / 2);
        }
    },
    methods: {
        existFlag(lang) {
            return this.flagsAviable.includes(lang);
        }
    }
}
</script>