<template>
    <svg viewBox="0 0 500 500" xmlns="http://www.w3.org/2000/svg" xmlns:bx="https://boxy-svg.com">

        <!-- BOAT -->
        <path
            d="M 229.727 169.94 L 249.967 265.122 L 209.487 265.122 L 229.727 169.94 Z"
            bx:shape="triangle 209.487 169.94 40.48 95.182 0.5 0 1@e27a41c4"
        />
        
        <!-- MAIN -->
        <rect
            class="sail"
            x="227.597"
            y="221.946"
            width="3.94"
            height="39.522"
            :transform="`rotate(${sailAngle} 227.597 221.946)`"
        />
        
        <!-- JIB -->
        <rect
            class="sail"
            x="227.836"
            y="181.52"
            width="3.431"
            height="26.789"
            :transform="`rotate(${running ? -sailAngle : sailAngle} 227.836 181.52)`"
           
        />

    </svg>
</template>

<script>
export default {
    props: {
        sailAngle: {
            type: Number,
            required: true,
        },
        course: {
            type: Number,
            required: true,
        },
    },
    computed: {
        running() {
            const n = Math.abs(this.course)%360
            console.log(n)
            return n > 165 && n < 195
        }
    }
}
</script>

<style scoped>
    svg {
        position: absolute;
    }

    .sail {
        fill: black;
    }
</style>