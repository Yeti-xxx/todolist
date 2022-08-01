<template>
    <div class="mt-3 btn-container">
        <div class="btn-group" role="group" aria-label="Basic example">
            <button @click="onBtnClick(0)" type="button" class="btn " :class="active === 0 ? 'btn-primary' : 'btn-secondary'">全部</button>
            <button @click="onBtnClick(1)" type="button" class="btn " :class="active === 1 ? 'btn-primary' : 'btn-secondary'">已完成</button>
            <button @click="onBtnClick(2)" type="button" class="btn " :class="active === 2 ? 'btn-primary' : 'btn-secondary'">未完成</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TodoButton',
    props: {
        active: {
            type: Number,
            required: true,
            default: 0,//全部0 已完成1 未完成2
        }
    },
    data() {
        return {
            
        }
    },
    emits: ['update:active'],
    methods: {
        onBtnClick(index){
            if (index===this.active) {
                return;
            }
            this.$emit('update:active',index);
        }
    }
}

</script>

<style lang='less' scoped>
.btn-container {
    width: 800px;
    text-align: center;
}

.btn {
    width: 100px;
}
</style>
