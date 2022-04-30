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
            transform="matrix(0.838671, -0.544639, 0.544639, 0.838671, -83.873947, 160.846283)"
            bx:origin="0.5 0.001366"
        />
        
        <!-- JIB -->
        <rect
            class="sail"
            x="227.836"
            y="181.52"
            width="3.431"
            height="26.789"
            transform="matrix(0.83867, -0.54464, 0.54464, 0.83867, -62.018322, 154.629074)"
            bx:origin="0.63072 0.017918"
        />

    </svg>
</template>

<style scoped>
    svg {
        position: absolute;
    }

    .sail {
        fill: black;
    }
</style>