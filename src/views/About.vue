<template>
    <div>
        <div v-if="!isMobile" class="ml-3 mr-3">
            <about-web/>
        </div>
        <div class="grid-list-sm pa-0" v-else>
            <about-mobile/>
        </div>
    </div>
</template>

<script>
import AboutWeb from './AboutW.vue'
import AboutMobile from './AboutM.vue'
export default {
    name: 'About',
    components: {
        AboutWeb,
        AboutMobile
    },
    data: () => ({
        isMobile: false
    }),
    beforeDestroy () {
        if (typeof window !== 'undefined') {
            window.removeEventListener('resize', this.onResize, { passive: true })
        }
    },
    mounted () {
        this.onResize()
        window.addEventListener('resize', this.onResize, { passive: true })
    },
    methods: {
        onResize () {
            this.isMobile = window.innerWidth < 600
        }
    }
}
</script>

<style scoped>
.about {
    max-width: 1050px;
}
.v-card-container {
    box-shadow: none;
    width: 50%;
}
.apple-sandol-font {
    font-family: "APPLE SD Gothic Neo",'Apple';
    font-size: 18px;
    font-weight: 400;
    line-height: 30px;
}
.apple-sandol-font.gray {
    color: #666765;
}
.introduce-context {
    margin: 48px 0;
}
.photo-card {
    width: 140px;
    height: 140px;
    margin: 0 5px;
}

.introduce-context .left-side {
    display: table-cell;
    text-align: left;
    vertical-align: top;
    color: #00000040;
    /* width: 450px; */
}

.introduce-context .right-side {
    display: table-cell;
    text-align: left;
    color: #000000;
    /* width: 520px; */
}
.right-side .small-logo {
    margin-bottom: 15px;
}
</style>