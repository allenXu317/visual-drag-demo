<template>
    <div class="component-list" @dragstart="handleDragStart">
        <div
            v-for="(item, index) in componentList"
            :key="index"
            class="list"
            draggable
            :data-index="index"
        >
            <span class="iconfont" :class="'icon-' + item.icon"></span>
        </div>
    </div>
</template>

<script>
import componentList from '@/custom-component/component-list'

export default {
    data() {
        return {
            componentList,
        }
    },
    methods: {
        handleDragStart(e) {
            e.dataTransfer.setData('index', e.target.dataset.index)
        },
    },
}
</script>

<style lang="scss" scoped>
.component-list {
    height: 65%;
    padding: 10px;
    display: grid;
    grid-gap: 10px 19px;
    grid-template-columns: repeat(auto-fill, 80px);
    grid-template-rows: repeat(auto-fill, 40px);

    .list {
        width: 80px;
        height: 40px;
        border: 1px solid #ddd;
        cursor: grab;
        text-align: center;
        color: #333;
        padding: 2px 5px;
        display: flex;
        align-items: center;
        justify-content: center;

        &:active {
            cursor: grabbing;
        }

        .iconfont {
            margin-right: 4px;
            font-size: 20px;
        }

        .icon-wenben,
        .icon-tupian {
            font-size: 18px;
        }
    }
}
</style>
